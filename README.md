# LDA y árboles de decisión

Este trabajo es un dataset de la INEGI ya limpiado previamente de errores llamado pib_turismo.csv.


DATASET:

- Archivo: pib_turismo.csv
  
- Forma: 1860 filas × 5 columnas
  
- Columnas: anio, tipo_precio, unidad_medida, categoria_detalle, valor_millones_pesos
  
- Para el plano 2D uso solo dos variables numéricas: anio y valor_millones_pesos.
  
- Construyo una clase binaria con la mediana del conjunto de entrenamiento:
  
  0 = Bajo, 1 = Alto según valor_millones_pesos relativo a la mediana del train.

INSTRUCCIONES:

- Carga y vista rápida

  Se lee el CSV, verifica forma (1860×5) y columnas. Confirmo que anio y valor_millones_pesos existen.

- Selección de variables + rango

  Me quedo con anio y valor_millones_pesos. Imprimo el rango de valor_millones_pesos para dimensionar la escala.

- Split 70/30 + clase binaria

  Hago train_test_split (70%/30%). Con solo train calculo la mediana y genero y: 0=Bajo, 1=Alto. Imprimo proporciones de clases en train y test para demostrar balance.

- Estandarización (z-score)
 
  Con StandardScaler creo anio_z y valor_millones_pesos_z. Esto deja ambas variables en la misma escala para trazar fronteras y evitar sesgos por magnitud.

- GLM (statsmodels)

  Regresión logística binaria con anio_z y valor_millones_pesos_z. Se imprime el summary() del modelo para documentar y justificar las dos variables que se usarán en las visualizaciones y en los clasificadores 2D.

- LDA (2D)

 Entrenamiento de LDA con las dos variables estandarizadas y gráfica de:

  - Puntos de entrenamiento coloreados por clase.

  - Frontera lineal (línea de decisión).

- Selección de α para poda (árbol)

  Cálculo del cost_complexity_pruning_path y selección de ccp_alpha mediante validación cruzada KFold(4) (criterio: mayor accuracy promedio; en empate se favorece el menor α).

- Árbol podado

  Entrenamiento del árbol con el α óptimo y dos visualizaciones:

  - Estructura del árbol (vista parcial para legibilidad).

  - Particiones 2D (regiones de decisión en el plano anio_z–valor_millones_pesos_z).

- Evaluación en prueba (LDA y Árbol)

  En el conjunto de prueba se imprimen para cada modelo:

    - Accuracy, Precision, Recall, F1

    - Matriz de confusión

    - classification_report
      

En la actividad se utilizan 3 documentos:


  
