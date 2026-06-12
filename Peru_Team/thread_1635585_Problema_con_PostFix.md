---
title: "Problema con PostFix"
date: 2010-12-02
forum: Peru Team
---

### Post by revenger98 on 2010-12-02
Buenas ....
Estoy tratando de instalar un mailserver con ubuntu 10 para mi trabajo.
Hasta ahora he podido hacer que funcione con lo que he podido leer en los forums de ubuntu.
Pero me he encontrado con un problema que espero me puedan guiar uds en algo q de seguro me falta hacer:

    * El servidor ya esta registrado como MX de mi dominio.
    * Envia y recibe emails a travez del cliente Web squirrelmail sin ningun problema, incluso con hotmail y yahoo, etc.
    * si hago telnet al port 25 en el mismo servidor obtengo respuesta.
    * si hago telnet al port 25 desde otra pc dentro de la misma red obtengo respuesta.
    * si hago telnet al port 25 desde una pc fuera de la red no ingreso aun cuando si ingrese al web squirrelmail.
    * intente ingresar con thunderbird pero me da como respuesta que no ingresa al servidor asumo que no se conecta al 25.
    * si hago : nmap -sS -r xx.xx.xx.xx EN EL MISMO SERVIDOR obtengo esto
    * Not shown: 991 closed ports
      PORT     STATE SERVICE
      22/tcp   open  ssh
      25/tcp   open  smtp
      53/tcp   open  domain
      80/tcp   open  http
      110/tcp  open  pop3
      143/tcp  open  imap
      993/tcp  open  imaps
      995/tcp  open  pop3s
      2000/tcp open  callbook
    * si hago el mismo nmap desde una PC fuera de la red obtengo esto
    * Not shown: 985 closed ports
      PORT     STATE    SERVICE
      22/tcp   open     ssh
      25/tcp   filtered smtp
      53/tcp   open     domain
      80/tcp   open     http
      110/tcp  open     pop3
      135/tcp  filtered msrpc
      139/tcp  filtered netbios-ssn
      143/tcp  open     imap
      445/tcp  filtered microsoft-ds
      593/tcp  filtered http-rpc-epmap
      993/tcp  open     imaps
      995/tcp  open     pop3s
      2000/tcp open     callbook
      4444/tcp filtered krb524
      6129/tcp filtered unknown
    * Vean que el stmp 25 aparece como filtrado (filtered), aun cuando el UFW esta disable.
    * He chequeado mi router (robofonica) y su firewall esta deshabilitado.
    * En la instalacion de postfix segui las instrucciones para habilitar SASL que segun creo es SMTP over SSL q deberia abrir el puerto 465 lo cual no se produjo creo.
    * Desde mi casa con thunderbird puedo ingresar al servidor y leer el correo mas no enviar,

Pregunto:
Sera posible habilitar el port 25 para smtp simple?
Sera posible habilitar el port 465 para smtp ssl ?
Cual seria la forma optima de habiltiar el envio de correo?

Gracias por sus aportaciones
Atte

fernando.guerra

---

### Post by waltervalderrama on 2011-01-07
Hola:

Tu servidor tiene una dirección IP pública directa en su interfaz o accede a internet a través de un router? De ser así, revisa las reglas de NAT, sobre todo las DNAT, que habilita puertos desde el exterior hacia las redes internas.

---

