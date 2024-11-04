
# Levantar un clúster de Hadoop + YARN + Hive. Hacer pruebas con consultas básicas SQL.

### Paso 1: Clonar y Configurar el Repositorio
Primero, clona el repositorio que contiene un contenedor de Hive:

```bash 
git clone big-data-europe/docker-hive 
cd docker-hive 
docker-compose up -d
```
Este paso puede llevar un tiempo, ya que Docker descargará todas las imágenes y configurará Hive. Para verificar que los contenedores se están ejecutando, usa:
```bash 
docker container ps
```

### Paso 2: Cargar y Consultar Datos en Hive

Accede al contenedor de nombre hive-server:
```bash 
docker-compose exec hive-server bash
```
Esto abre una terminal en el contenedor de Hive, desde donde puedes ejecutar comandos de Hive usando Beeline, el cliente JDBC de Hive.

Inicia beeline:
```bash 
# /opt/hive/bin/beeline -u jdbc:hive2://localhost:10000
```

### Paso 3: Crear la base de datos

```bash 
> CREATE TABLE pokes (foo INT, bar STRING);
> LOAD DATA LOCAL INPATH '/opt/hive/examples/files/kv1.txt' OVERWRITE INTO TABLE pokes;
```
### Paso 4: Consulta basica para probar que se ha creado la base datos

```bash 
select * from pokes;
```

