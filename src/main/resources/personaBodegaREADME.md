# PersonalBodegaServiceImp

Este componente forma parte del sistema de gestión de personal de bodega. Implementa la lógica de negocio para operaciones CRUD sobre el personal encargado de bodega, haciendo uso de Spring Boot, DTOs y mapeo de entidades.

## 📦 Paquete
`co.edu.uniquindio.service.impl`

## 📚 Descripción

`PersonalBodegaServiceImp` es una clase de servicio que implementa la interfaz `PersonalBodegaService`. Gestiona la creación, edición, eliminación, obtención y listado paginado del personal de bodega utilizando un repositorio JPA (`PersonalBodegaRepository`) y un mapper (`PersonalBodegaMapper`) para la conversión entre entidades y DTOs.

## 🛠️ Funcionalidades

- **Crear Personal de Bodega**  
  Valida que no exista email ni cédula duplicada. Convierte el DTO a entidad y lo guarda en la base de datos.

- **Obtener Personal por ID**  
  Busca por cédula en la base de datos y retorna un DTO. Lanza excepción si no lo encuentra.

- **Actualizar Personal de Bodega**  
  Busca la entidad por ID, actualiza los datos y guarda los cambios.

- **Eliminar Personal de Bodega**  
  Verifica si existe y elimina por ID.

- **Listar Personal de Bodega (Paginado)**  
  Retorna una lista paginada (5 elementos por página) del personal en forma de DTOs.

## 📄 Estructura de DTOs

- `CrearPersonalBodegaDTO`: DTO para crear nuevos registros.
- `EditarPersonalBodegaDTO`: DTO para editar datos existentes.
- `PersonalBodegaDTO`: DTO de salida para representar información del personal.

## ⚠️ Excepciones

- `ElementoNoEncontradoException`: Se lanza cuando se intenta acceder a un personal que no existe en la base de datos.
- `Exception`: Genéricas para errores de validación como email o cédula duplicada.

## 🧪 Dependencias

- `Spring Boot`
- `Spring Data JPA`
- `Lombok`
- `MapStruct` (u otro mapper)
- `Java 17+`

## ✨ Ejemplo de Uso

```java
@Autowired
private PersonalBodegaService personalBodegaService;

public void registrar() throws Exception {
    CrearPersonalBodegaDTO dto = new CrearPersonalBodegaDTO("123", "juan@mail.com", "Juan", "Pérez");
    personalBodegaService.crearPersonalBodega(dto);
}
