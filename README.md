# Chat dialogs labelling - Final project Text Mining

### Objetivo

Dado un conjunto de textos proveniente de una conversación queremos identificar y etiquetar temas que se fueron hablando en distintas secciones del chat.

Por ejemplo: Supongamos que al programa (Clasificador), le damos como entrada una conversación entre 2 personas. El objetivo es que podamos obtener de una manera visual las secciones con etiquetas de los diferentes temas hablados en esa conversación.

![](images/sample_nico.png)

En la imagen anterior podemos ver un ejemplo de una conversacion, lo que nosotros esperamos es que el modelo pueda identificar esta parte de la conversación con temas relacionados a la universidad, estudio, etc.

![](images/sample_nico_labeled.png)

### Aproximación al problema

Cuestiones para tener en cuenta en el proyecto es que las etiquetas van a estar fijas y van a ser en base al corpus de entrenamiento. Este corpus de entrenamiento debe ser generado a partir de conversaciones personales.

El primer paso en el proyecto es la obtención del Corpus. Este paso se dificulta por el hecho de que las conversaciones son personales. Una forma de obtener chats fue recolectar conversaciones de grupos de whatsapp y chats propios.

La idea del approach es de utilizar un corpus para etiquetar conversaciones y con esos ejemplos ya etiquetados poder entrenar un clasificador. La forma de etiquetar estas conversaciones que luego se usaran para entrenar el clasificador es a partir de un algoritmo de clustering en el cual a partir de los elementos de cada cluster, se generaliza el tema y se usa esa etiqueta para cada elemento de ese cluster.

Se tiene que destacar que la mayor parte del proyecto consiste en generar estos ejemplos para el clasificador, ya que de esto dependera gran parte la calidad de las predicciones.



### Diagrama de flujo

![](images/flujo.png)

#### Preprocesamiento

El objetivo de este paso es normalizar el corpus. Este paso nos permitira obtener mejores resultados en las siguientes etapas, es una parte crítica para el proyecto. Dentro de las acciones realizadas tenemos:

*  Creación de unidad, los cuales son conjuntos de mensajes enviados sin interrupción por un mismo usuario, con un threshold de X minutos (En nuestro caso se utilizó 10 minutos). 
*  Normalizar palabras utilizando expresiones regulares. Las acciones fueron las siguientes:
  *  Eliminar caracteres repetidos. **Ejemplo** 'holaaaa' por 'hola'
  *  Omitir media
  *  Remplazo de abreviaciones por la palabra completa. **Ejemplo** 'hno' por 'hermano'.
*  Remover stopwords, dígitos y palabras con menos de 3 caracteres.
*  Remover palabras que aparecen menos de 3 veces en todo el corpus.
*  Lematización. Este paso nos permite remplazar palabras por su raiz. **Ejemplo** 'corriendo' por 'correr'
*  Remover unidades con menos de Y palabras (Luego del preprocesamiento anterior). (NO IMPLEMENTADO)

### ** EN ALGUN LADO TIENE QUE ENTRAR SCALING

#### Embeddings

* BAG con TF-IDF

* Doc2Vec gensim

* Promedio con embeddings con fastText (uso de subwords)

#### Clustering


### Datos de ejemplo

![](images/sample_chat.png)

- Aca se muestra una captura del corpus antes del procesamiento. 

### Topic detection en clustering.

### Topic discovery

### Aplicacion de retrieval o de que se habla en este grupo

### Visualization

*** Conversaciones en las que se habla este tema, snipet en el que se habla el tema (De la demo)

### Resultados y comparaciones

### Desafios

* Diferentes dominios

* Palabras mal escritas

* Palabras personalizadas

* Mensajes en multimedia que son parte de la conversacion

* Donde empieza y termina un tema no esta formalmente definido

* El corpus es de caracter personal por lo que dificulta la obtencion de ejemplos por temas de privacidad.

* No existe una unica etiqueta que englobe a la conversacion.


### Conclusiones

En el siguiente proyecto se pudo ver de una forma end-to-end el proceso de creación de un proyecto de mineria de datos. Desde el planteo del problema e idea de solución, hasta la ejecución de esta en los diferentes pasos como la obtención del corpus, su pre-procesamiento, las visualizaciones de los datos, la formas de evaluar la presición del mismo y como asi tambien lograr un prototipo.


### Trabajo a futuro

* Corpus más grande y especificos del lenguaje, (se puede incluir tweets en español de temas especificos para mejorar el corpus.)

* Investigar con Sent2Vec de gensim

* Mejorar el clusterizado

### Instalacion y uso

Instalación de requerimientos

`pip3 install -r requirements.txt`

### Referencias

- [Referencias de la propia materia.](https://sites.google.com/view/text-mining-2019/materiales?authuser=0)
- [Preprocesado de corpus](https://kavita-ganesan.com/text-preprocessing-tutorial/#.XjU0mhMzYmp)
- [Word2Vec y FastText Word Embedding en Gensim](https://towardsdatascience.com/word-embedding-with-word2vec-and-fasttext-a209c1d3e12c)
- [Introduccion a Doc2Vec](https://medium.com/wisio/a-gentle-introduction-to-doc2vec-db3e8c0cce5e)
- [Topic modelling](https://nlpforhackers.io/topic-modeling/)
- [Curso de NLP de stanford](http://web.stanford.edu/class/cs224u/)
- [Clasificador con regresion logistica](https://kavita-ganesan.com/news-classifier-with-logistic-regression-in-python/#.XjPCehMzYmo)
- [Regresion logistica en python](https://towardsdatascience.com/logistic-regression-using-python-sklearn-numpy-mnist-handwriting-recognition-matplotlib-a6b31e2b166a)
- [K-Means clustering](https://towardsdatascience.com/k-means-clustering-algorithm-applications-evaluation-methods-and-drawbacks-aa03e644b48a)
