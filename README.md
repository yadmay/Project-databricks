# Proyecto Final - Ingeniería de Datos con Databricks
Proyecto final curso Ingeniería de datos e IA con Databricks - SmartData - Estudiante: Yadira Rodriguez

Este proyecto implementa un flujo ETL completo utilizando **Databricks** y la arquitectura **Medallion** (Bronze → Silver → Gold).  El dataset utilizado corresponde a un sistema de compras en línea con múltiples tablas (customers, products, sales, etc.).

## Plan de implementación
- Raw: ingesta de los 7 CSV en Delta Lake con Managed Identity.
- Silver: unión de tablas, limpieza de datos y cálculo de métricas adicionales.
- Gold: agregación de ventas por categoría y cliente.
- CI/CD: pipeline en GitHub Actions que ejecuta los notebooks automáticamente.
- Visualización: conectar la capa Gold a una herramienta de BI.
- Entrega final: publicar el repositorio en GitHub con README, notebooks y workflows.

---

## 🚀 Flujo de trabajo

### 1. Ingesta (Bronze Layer)
- Se cargan los archivos CSV desde Azure Data Lake Storage.
- Se definen esquemas con `StructType` para validar los tipos de datos.
- Los datos se almacenan en formato **Delta Lake** en la capa *bronze*.

### 2. Transformación (Silver Layer)
- Se realizan uniones entre tablas (ejemplo: `sales` con `customers` y `products`).
- Se limpian y enriquecen los datos (ejemplo: cálculo de `TotalValue = Quantity * Price`).
- Se añade la columna `ingestion_date` para trazabilidad.
- Los resultados se guardan en la capa *silver*.

### 3. Agregación (Gold Layer)
- Se generan métricas de negocio listas para visualización.
- Ejemplo: ventas totales por categoría de producto y cliente.
- Los resultados se guardan en la capa *gold*.

### 4. CI/CD
- Se configura un pipeline en **GitHub Actions**.
- El pipeline ejecuta automáticamente los notebooks de Raw, Silver y Gold al hacer *push* en la rama principal.

### 5. Visualización
- La capa Gold se conecta a herramientas de BI de **Databricks SQL**.
- Se construyen dashboards con métricas clave:
  - Ventas por categoría.
  - Clientes con mayor volumen de compras.
  - Comparación de ventas por período de tiempo.
  Se encuentra publicado y exportado en formato .json

### 6. Entrega Final
- El repositorio incluye:
  - Notebooks de ingesta, transformación y agregación.
  - Workflows de CI/CD.
  - Esquemas en PySpark (`StructType`).
  - Este README.md con la documentación del flujo.

---

## 📂 Estructura del repositorio

- Datasets
- Dashboard
- Reversion
- .github/workflow
- Seguridad
- PreAmb
- proceso
- certificaciones
- Evidencias
- README.md
