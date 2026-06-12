---
title: "Problema al actualizar Ubuntu 9.10"
date: 2010-09-25
forum: Peru Team
---

### Post by wcruzy on 2010-09-25
Estimados señores:

Trato de actualizar el Ubuntu 9.10 o de descargar cualquier aplicación y se muestra el siguiente mensaje:

dpkg: error en el análisis, en archivo «/var/lib/dpkg/available» línea cercana 21906:
 nombre de paquete inválido (
E: Sub-process /usr/bin/dpkg returned an error code (2)


He vuelto a instalar el Ububtu 9.10 y el problema persiste, aún cuando trato de instalar paquetes desde el Centro de Software de Ubuntu

Espero su consejo para resolver esta terrible situación

Atentamente,

Wilfredo Cruz Y

---

### Post by genelyk on 2010-09-25
has  propbado haciendo " sudo dpkg-reconfigure -a "

---

### Post by davidsonxxi on 2010-10-20
Saludos.

por lo visto no especificas mucho sobre tu plataforma, pero por el aplicativo que usas debo suponer que es un server y no una version de escritorio.

el programa dpkg geeral mente se utiliza para instalar programas aliens (compatibles o de otro tipo de distribución o procedimientos adicionales de programas instalados) 

en el modo consola todo lo relacionado a ubuntu se encuentra en los repositorios y se trata con el programa apt-get

por ejemplo quieres instalar un editor de internet como el bluefish, debes escribir en modo consola lo siguiente:

sudo apt-get install bluefish

y el programa se encargará de descargar e instalar adecuadamente, incluyendo los programas adicionales necesarios

si necesitas ayuda sobre apt-get debes escribir lo siguiente:
sudo apt-get --help   
ojo debe ser doble guion o signo menos

sudo apt-get update    actualiza los repositorios por actualizaciones de la distribución
sudo apt-get upgrade   descarga los paquetes nuevos y los instalas

bueno puedes seguir urgando mucho con apt-get y después de familiarizarte pasar a dpkg

nota si tienes un escritorio GNOME tons la cosa es mas facil  sigue los pasos (en español):
Sistema / Administracion / Gestor de paquetes Synaptic

y desde alli realizas todas tus instalaciones de la dstribución.

Bye

Suerte.


adicionaes  
se lod
ç, pero debo 

> **wcruzy said:**
> Estimados señores:

Trato de actualizar el Ubuntu 9.10 o de descargar cualquier aplicación y se muestra el siguiente mensaje:

dpkg: error en el análisis, en archivo «/var/lib/dpkg/available» línea cercana 21906:
 nombre de paquete inválido (
E: Sub-process /usr/bin/dpkg returned an error code (2)


He vuelto a instalar el Ububtu 9.10 y el problema persiste, aún cuando trato de instalar paquetes desde el Centro de Software de Ubuntu

Espero su consejo para resolver esta terrible situación

Atentamente,

Wilfredo Cruz Y

---

