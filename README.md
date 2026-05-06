# CHAT SEGURO

Backend seguro para sistema de chat con autenticación JWT, cifrado de contraseñas y documentación Swagger.

## Tecnologías

- **Node.js** + **Express** - Framework del servidor
- **MongoDB Atlas** - Base de datos en la nube
- **Mongoose** - ODM para MongoDB
- **JWT** - Autenticación con tokens
- **Bcrypt** - Cifrado de contraseñas
- **Swagger** - Documentación interactiva de la API

## Estructura del Proyecto

```
CHAT-SEGURO/
├── backend/
│   ├── src/
│   │   ├── index.js              # Punto de entrada y rutas de la API
│   │   ├── models/
│   │   │   └── User.js           # Modelo de usuario (Mongoose)
│   │   └── middlewares/
│   │       └── auth.js           # Middleware de autenticación JWT
│   ├── .env                      # Variables de entorno
│   └── package.json              # Dependencias del proyecto
└── diagramas/
    ├── Chat Authentication and-2026-04-28-015247.pdf
    ├── Chat Authentication and-2026-04-28-015321.pdf
    ├── Chat Authentication and-2026-04-28-015353.pdf
    └── diagrama de Gant.pdf
```

## Endpoints de la API

### Autenticación

| Método | Ruta | Descripción | Autenticación |
|--------|------|-------------|---------------|
| POST | `/register` | Registrar nuevo usuario | No |
| POST | `/login` | Iniciar sesión | No |
| GET | `/profile` | Obtener perfil del usuario | Sí (Bearer Token) |

### Ejemplos de Uso

#### Registrar Usuario

```bash
curl -X POST http://localhost:3000/register \
  -H "Content-Type: application/json" \
  -d '{"username": "miusuario", "password": "mi_password"}'
```

**Respuesta exitosa (201):**
```json
{
  "message": "Usuario registrado",
  "userId": "67f8a1b2c3d4e5f6a7b8c9d0"
}
```

#### Iniciar Sesión

```bash
curl -X POST http://localhost:3000/login \
  -H "Content-Type: application/json" \
  -d '{"username": "miusuario", "password": "mi_password"}'
```

**Respuesta exitosa (200):**
```json
{
  "message": "Login exitoso",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

#### Obtener Perfil

```bash
curl -X GET http://localhost:3000/profile \
  -H "Authorization: Bearer <tu_token>"
```

**Respuesta exitosa (200):**
```json
{
  "user": {
    "userId": "67f8a1b2c3d4e5f6a7b8c9d0",
    "username": "miusuario",
    "iat": 1714982400,
    "exp": 1715068800
  }
}
```

## Documentación Swagger

Una vez iniciado el servidor, la documentación interactiva está disponible en:

```
http://localhost:3000/api-docs
```

## Instalación

1. **Clonar el repositorio**

```bash
git clone https://github.com/tc-felxpe/CHAT-SEGURO.git
cd CHAT-SEGURO/backend
```

2. **Instalar dependencias**

```bash
npm install
```

3. **Configurar variables de entorno**

Crear un archivo `.env` en la carpeta `backend/` con las siguientes variables:

```env
MONGO_URI=tu_conexion_a_mongodb
JWT_SECRET=tu_secreto_jwt_seguro
PORT=3000
```

4. **Iniciar el servidor**

```bash
# Desarrollo
npm run dev

# Producción
npm start
```

## Modelo de Usuario

```javascript
{
  username: String,    // Requerido, único
  password: String,    // Requerido, cifrado con bcrypt
  createdAt: Date      // Automático, fecha de creación
}
```

## Seguridad

- **Contraseñas cifradas** con bcrypt (salt rounds: 10)
- **Autenticación JWT** con expiración de 24 horas
- **Middleware de protección** para rutas sensibles
- **Validación de tokens** en cada请求 protegida

## Diagramas

El proyecto incluye diagramas en la carpeta `diagramas/`:

- Diagramas de autenticación y flujo de chat
- Diagrama de Gantt (planificación del proyecto)

## Dependencias

| Paquete | Versión | Propósito |
|---------|---------|-----------|
| express | ^4.18.2 | Framework web |
| mongoose | ^9.6.0 | ODM MongoDB |
| jsonwebtoken | ^9.0.3 | Generación/validación de tokens JWT |
| bcryptjs | ^3.0.3 | Cifrado de contraseñas |
| dotenv | ^17.4.2 | Variables de entorno |
| swagger-jsdoc | ^6.2.8 | Generador de especificación Swagger |
| swagger-ui-express | ^5.0.0 | Interfaz de documentación Swagger |

## Licencia

Este proyecto es de uso privado.
