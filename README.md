# LoadTest_PetStoreAPI
Este repositorio contiene un plan de pruebas para la API PetStore.
La prueba es No Funcional la cual dura 10 minutos. Realiza una carga escalonada de 500 hilos durante los primeros 8 minutos y despues se sotiene por dos minutos mas.
El artefacto de la prueba es un script de Jmeter utilizando el tipo de hilo Currency Thread Group.
El script cuenta con 3 listener: Resumen, Arbol de resultados y PerfMon Metrics Collector.  Este ultimo se encarga de colectar los datos del comportamiento de los recursos de la maquina en un formato legible por Nmon. 
Esto estilo de recoleccion de datos de Performance (comportamiento del host), solo es posible, debido a que el agente de pruebas es el mismo host de la aplicacion. Esto no es lo mas recomendable para una prueba, solo se realiza a modo de demostracion; en un escenario mas real, el host debe ser diferente del agente de pruebas. 


## 📋 Requisitos
* El script en Jmeter fue desarrollado para la version 5.6.3 
* Java 17

## 🚀 Pipeline de Ejecucion en GibhubActions
El pipeline descarga la aplicacion bajo prueba de la siguiente url:
`https://github.com/swagger-api/swagger-petstore.git`, la ejecuta y comprueba que este disponible.
Tambien descarga Jmeter. Descarga e instala los plugins utilizados en el script.
Igualmente descarga, configura y ejecuta PerfMon ServerAgent.
Una vez este todo configurado, ejecuta la prueba y genera el reporte HTML.

El pipeline corre en sistema operativo Ubuntu 24.04. Sin embargo, la automatizaicon podria usarse en entornos windows o cualquier otra distribucion Linux.
