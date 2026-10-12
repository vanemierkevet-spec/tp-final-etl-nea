# TP Final – Pipeline ETL de exportaciones del NEA

**Unidad II – Fundamentos de la Programación**  
Diplomatura en Data Analytics e IA Aplicada – UNNE / Extender

## Descripción del proyecto

Este trabajo consiste en desarrollar un pipeline ETL (extracción, transformación y carga) utilizando Python y datos públicos de exportaciones de las provincias del Nordeste Argentino (NEA): Chaco, Corrientes, Formosa y Misiones.

El objetivo es obtener información de una API pública, procesarla y generar un archivo CSV que pueda utilizarse posteriormente para el análisis de datos.

## Fuente de datos

Se utilizó la API de Series de Tiempo de datos.gob.ar, con información del INDEC sobre exportaciones por país de destino y por rubro.

El período analizado comprende los años 1993 a 2024.

## Funcionamiento del pipeline

El proceso está organizado en tres etapas:

1. **Extracción (Extract):** se consultan los datos de las cuatro provincias mediante ocho descargas desde la API.
2. **Transformación (Transform):** se organizan los registros y se calculan nuevas variables, como región de destino, década, participación porcentual, variación interanual y ranking de destinos. También se incorpora información sobre los rubros de exportación.
3. **Carga (Load):** se realizan controles de calidad y se generan los archivos de salida.

## Resultados obtenidos

En la ejecución del 12 de octubre de 2026 se obtuvieron:

- **1.247 registros**.
- **13 columnas**.
- Información de **cuatro provincias**.
- Período comprendido entre **1993 y 2024**.
- **8 de 8 descargas** completadas correctamente.

El archivo principal generado es `data/processed/exportaciones_nea.csv`.

También se genera `data/processed/resumen.json`, con información general de la ejecución, y `logs/pipeline.log`, con el registro del proceso.

## Controles de calidad

Se verificaron la cantidad mínima de registros, la presencia de las 13 columnas, la ausencia de duplicados y la plausibilidad de los valores.

Todos estos controles finalizaron correctamente.

El proceso también informó dos observaciones: 171 filas sin variación interanual y 154 filas sin información de rubro. Estas situaciones quedaron registradas como avisos y no impidieron completar el pipeline.

## Cómo ejecutar el proyecto

Desde la carpeta `tp-final/template`, ejecutar:

```bash
python src/main.py
```

Para ejecutar las pruebas:

```bash
python -m unittest discover -s tests -v
```

## Pruebas realizadas

Se ejecutaron 19 pruebas: **17 finalizaron correctamente y 2 quedaron omitidas**, correspondientes a las pruebas adicionales del TODO 13.

El pipeline completo finalizó correctamente, generando el CSV, el resumen y el archivo de registro.

## Conclusión

Este trabajo permitió aplicar contenidos de programación en Python, como funciones, listas, diccionarios, bucles, condiciones y manejo de archivos.

También permitió comprender cómo se organiza un proceso ETL y la importancia de validar los datos antes de utilizarlos para realizar análisis posteriores.