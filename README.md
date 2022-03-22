# Generic Docker Mongo Parse Server with Dashboard 
This project lets you create a MongoDB database, a Parse server and a Parse Dashboard using Docker. 
Cloun Functions and Live Queries are enabled. 
## Installation
1) Install Docker https://www.docker.com/
2) Open console in the current directory and digit the following command to create a docker instance: 
    ```console
    (sudo) docker-compose up -d
    ```
3) Check if the instances are correclty working using Docker Desktop or running the following command: 
    ```console
    docker ps -a
    ```
5) Access to the dashboard through this link: <http://localhost:4040/>. Username: user, Password: pass (configurable through `PARSE_DASHBOARD_USER_ID` and `PARSE_DASHBOARD_USER_PASSWORD` environment variables in docker-compose.yml)
4) If the dashboard doesn't work, please insert the following entry on the hosts file (for windows, C:\Windows\System32\drivers\etc\hosts):
    ```
    127.0.0.1 parse
    ```

## Live Queries
Live queries are enabled by default. 
Le live queries sono già attivte. To make it work it is necessary:
- Setting the variable `PARSE_SERVER_START_LIVE_QUERY_SERVER=1`
- Setting the variable `PARSE_SERVER_LIVE_QUERY` and assign to it the list of all classes who are providing the Live Query service. For example:
    ```
    PARSE_SERVER_LIVE_QUERY={"classNames":["commesse", "impiegati"]}
    ```
    provides the live queries for the classes "commesse" and "impiegati".

## Cloud Functions
Cloud fnctions are enabled by default. They are defined in cloud/main.js. To let them work you have to enable `PARSE_SERVER_CLOUD` environment variable specifying the path of the main.js file. The command nder the `volumes` key allows you to copy main.js file from local to docker folder.
    
# Docker Mongo Parse Server con Dashboard ITA
Questo progetto consente l'installazione di un database mongodb, un server Parse ed una dashboard per il controllo del server. Qui sono abilitate le live query e le cloud functions. 

## Installazione
1) Installare Docker https://www.docker.com/
2) Modificare le variabili con *** nel file docker-compose.yml. Queste variabili sono specifiche di ogni progetto e devono essere impostate con estrema cura. 
3) Aprire il terminale nella cartella ed eseguire il comando  
    ```console
    (sudo) docker-compose up -d
    ```
4) Controllare che il progetto funzioni da Docker Desktop oppure eseguendo il comando 
    ```console
    docker ps -a
    ```
5) Accedere alla dashboard tramite l'indirizzo <http://localhost:4040/>. Username: user, Password: pass (configurabile impostando le variabili di ambiente `PARSE_DASHBOARD_USER_ID` e `PARSE_DASHBOARD_USER_PASSWORD` nel file docker-compose.yml)
6) Se la dashboard non va, aggiungere una entry nel file hosts (C:\Windows\System32\drivers\etc\hosts)
    ```
    127.0.0.1 parse
    ```

## Live Queries
Le live queries sono già attivte. Per farle funzionare è necessario:
- Settare il valore della variabile `PARSE_SERVER_START_LIVE_QUERY_SERVER=1`
- Settare il valore della variabile `PARSE_SERVER_LIVE_QUERY` con l'elenco dei nomi delle classi nel DB che dovranno fornire il servizio di live query. Per esempio:
    ```
    PARSE_SERVER_LIVE_QUERY={"classNames":["commesse", "impiegati"]}
    ```
    fornisce il servizio di live query alle classi con nome "commesse" ed "impiegati".

## Cloud Functions
Le cloud functions sono già attive di default. Il parametro che permette l'attivazione nel docker-compose è 
`PARSE_SERVER_CLOUD` che permette di specificare il path da cui prendere il file delle funzioni cloud. Il 
comando sotto la chiave `volumes` consente di copiare il file main.js dalla cartella locale al docker. 

## TODO: Aggiungere la password! 
(Nel file FUNZIONANTE la password va, ma appena si prova a morificarla non funziona più >:(