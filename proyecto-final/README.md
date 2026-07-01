# Evaluación: Diseño e Implementación de Base de Datos - "ACME Copropiedades"

## 1. Contexto del Requerimiento
Se solicita diseñar e implementar una base de datos relacional para una empresa administradora de condominios y edificios de copropiedad. El sistema debe ser capaz de modelar de manera fiel la realidad operativa, las restricciones de negocio y la gobernanza interna de las distintas comunidades asociadas.

---

## 2. Descripción del Problema
El sistema propuesto debe contemplar e integrar de forma estricta las siguientes reglas de negocio:

* **Comunidades y Áreas:** La empresa administra diferentes **Comunidades** (edificios o condominios). Cada comunidad posee un nombre único, una dirección (ubicación) y un empleado asignado como "Administrador General". Es imperativo registrar la fecha exacta en la que dicho administrador comenzó a dirigir la comunidad.
* **Áreas Comunes y Mantenciones:** Cada comunidad cuenta con diversas **Áreas Comunes** (ej: quinchos, piscinas, lavanderías, gimnasios). De cada una interesa saber su nombre, metros cuadrados y tipo de área. Una comunidad puede no tener áreas comunes. Para asegurar el correcto funcionamiento de estos espacios, se realizan **Mantenciones** periódicas; el sistema debe registrar el costo, la descripción detallada del trabajo y la fecha en que se ejecutó.
* **Departamentos y Estacionamientos:** Cada comunidad está compuesta por múltiples **Departamentos**. De cada uno se registra su número de unidad, metros cuadrados, porcentaje de prorrateo (gasto común) y si está actualmente habitado por sus dueños o es arrendado. Adicionalmente, el condominio cuenta con **Estacionamientos**, cada uno con su respectivo número y tipo (subterráneo, visitas o superficie). Todo departamento y estacionamiento debe estar asignado obligatoriamente a una sola comunidad.
* **Personas y Propiedad Multi-unidad:** Se mantiene un registro de las **Personas** relacionadas con el condominio, guardando su nombre completo, RUT, dirección de correspondencia, salario, sexo y fecha de nacimiento. Todo residente debe estar asignado a un departamento base. Sin embargo, el modelo debe permitir que una persona sea **propietaria de múltiples departamentos y/o estacionamientos** en la comunidad, los cuales no necesariamente coinciden con la unidad donde reside actualmente.
* **Uso de Áreas Comunes:** Se desea llevar un control estricto de la ocupación de los espacios públicos. El sistema debe registrar de forma histórica el número de horas por semana que un residente dedica o reserva para cada área común específica.
* **Comité de Administración (Supervisión):** Para la resolución de conflictos y mediación interna, se requiere saber qué miembro del Comité de Administración actúa como "Supervisor Directo" de cada residente. Todo supervisor es a su vez un residente, pero no todo residente pertenece al comité ni es supervisor.
* **Cargas Familiares (Seguros):** Se requiere mantener información de los **Familiares** de cada residente con el objetivo de administrar las pólizas de seguros de accidentes en espacios comunes. De cada familiar interesa el nombre completo, sexo, fecha de nacimiento, edad y el parentesco con el residente principal.
* **Gastos Comunes:** El sistema debe gestionar las finanzas de la comunidad. Mensualmente se genera un "Gasto Común General" por comunidad (indicando mes, año y monto total acumulado de gastos del periodo). A partir de este monto global, y utilizando el **porcentaje de prorrateo** de cada departamento, el sistema debe calcular automáticamente y emitir el cobro individual por cada departamento, registrando el valor resultante, la fecha de vencimiento y el estado actual del pago (valores posibles: *Pendiente*, *Pagado*, *Atrasado*).

---

## 3. Entregables Solicitados

Los estudiantes deberán desarrollar e integrar en su entrega final los siguientes artefactos técnicos:

### I. Diagrama Entidad-Relación (DER)
* Modelo conceptual completo utilizando notación formal (Chen o Crow's Foot).
* Debe explicitar: Entidades (fuertes y débiles), atributos (identificando claves primarias `PK`), relaciones, cardinalidades ($1:1$, $1:N$, $M:N$) y restricciones de participación (opcional/obligatoria).

### II. Modelo Relacional
* Pasaje del DER a tablas lógicas normalizadas.
* Formato de entrega requerido para cada tabla:
  `Nombre_Tabla (Clave_Primaria, Atributo1, Atributo2, ..., Clave_Foranea#)`
* Declaración explícita de las restricciones de Integridad Referencial (claves foráneas `FK` y tablas a las que apuntan).

### III. Análisis de Normalización
* Demostración analítica y justificación de cómo el diseño relacional propuesto cumple con las **Formas Normales** fundamentales:
  * **Primera Forma Normal (1FN):** Ausencia de grupos repetitivos y atributos multivalorados.
  * **Segunda Forma Normal (2FN):** Cumplimiento de 1FN y dependencia funcional completa de los atributos respecto a la clave primaria.
  * **Tercera Forma Normal (3FN):** Cumplimiento de 2FN y ausencia de dependencias transitivas.

### IV. Base de Datos Física en SQLite
* **Archivo de Base de Datos:** Un archivo binario válido con extensión `.db` ejecutable en SQLite.
* **Script SQL (`.sql`):** El código fuente que contenga todas las sentencias `CREATE TABLE` utilizadas. El script debe implementar de forma rigurosa:
  * Los tipos de datos nativos de SQLite (`INTEGER`, `REAL`, `TEXT`, `NUMERIC`, etc.).
  * Restricciones de columna básicas (`PRIMARY KEY`, `FOREIGN KEY`, `NOT NULL`, `UNIQUE` e integridad en cascada si corresponde).

---
