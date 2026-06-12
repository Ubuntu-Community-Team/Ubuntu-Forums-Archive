---
title: "Cargar aplicaciones ubuntu en memoria flash"
date: 2011-06-13
forum: Peru Team
---

### Post by BiosDaddy on 2011-06-13
Hola, soy nuevo en el foro
Tengo un problema al querer instalar la aplicacion QtQr en una memoria flash a la cual le he cargado ubuntu 11.04.
La memoria flash bootea normal, todo funciona, la aplicacion la he cargado sin problemas en otra pc con la misma version de ubuntu, pero la querer instalarla en la memoria flash me dice que faltan librerias o dependencias o algo por el estilo.
He intentado instalar las dependencias una por una pero siempre sale que falta alguna otra.
Alguna idea o ayuda al respecto, se los agradeceria bastante.

Saludos

---

### Post by ddi4z on 2011-08-02
He ingresado a su página oficial: [http://code.google.com/p/qtqr/](http://code.google.com/p/qtqr/)
Allí te dice que las dependencias que necesitas son las siguientes:
zbar for decoding
PIL for decoding
PyQt4
Python 2.6

Puedes buscar y asegurarte de descargarlas  individualmente desde aquí: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Ojalá te sirva ;)

---

### Post by genelyk on 2011-08-05
eso es normal q te pidan dependencia tras dependencia, alegrate q no te pidan una antigua q no esta soportada.
en la otra maquina esta instalado via  apt-get o lo bajaste de inter con algun deb

---

