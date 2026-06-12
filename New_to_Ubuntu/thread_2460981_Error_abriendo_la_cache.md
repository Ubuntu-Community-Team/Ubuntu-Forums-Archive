---
title: "Error abriendo la cache"
date: 2021-04-22
forum: New to Ubuntu
---

### Post by yosemi44 on 2021-04-22
Hola:

Tengo el ubuntu 18.04.5 LTS y me sale este error:

Error abriendo la cache (E: Unable to parse package file /var/lib/aptestendede_states(1)

¿Qué puedo hacer?

---

### Post by aromo2 on 2021-04-22
Hola,

Si quieres una respuesta util, ayudanos a ayudarte. En donde te sale el error? Que haces para que salga? Da mas detalles por favor.

---

### Post by yosemi44 on 2021-04-22
Me aparece el error cuando ya ha arrancado el ubuntu.
Me sale una pantalla  que me dice que se ha detectado un problema en un programa del sistema ¿Quiere informar de este problema ahora?  y le doy a informar del problema.
Cuando hago un sudo apt upgrade -y me sale este mensaje:
E: Se interrupio la ejecucion de dpkg, debe ejecutar manualmente sudo dpkg --configure -a para corregir el problema, y me dice:
dpkg: error: al analizar el fichero ' / var/lib/dpkg/updates/0000 ' cerca de la línea 0: el nombre del campo ' imagen de un cuadradito ' debe estar seguido por dos puntos.

---

### Post by grahammechanical on 2021-04-22
According to google translate. Post #1

> Error opening cache (E: Unable to parse package file / var / lib / aptestendede_states (1)

Post #2

> If you want a useful answer, help us to help you. Where do you get the error? What do you do to get it out? Give more details please.

Post #3

> I get the error when the ubuntu has already started.I get a screen that tells me that a problem has been detected in a system program. Do you want to report this problem now? and I give you to report the problem.When I do a sudo apt upgrade -y I get this message:E: The execution of dpkg was interrupted, you must manually execute sudo dpkg --configure -a to correct the problem, and it tells me: dpkg: error: when analyzing the file '/ var / lib / dpkg / updates / 0000' near line 0: the name of the field 'image of a square' must be followed by a colon.

Regards

P.S. On my 20.04 system the folder /var/lib/dpkg/updates is empty.  I am guessing that /var/lib/aptestendede_states is actually /var/lib/apt/extended_states.

---

### Post by QIII on 2021-04-22
Hello!

This is an English speaking area of the Forums.  Please post in English (including responses) -- even if you are not very good at it.  We understand that not everyone who seeks help happens to speak English.  We will still attempt to help as best we can.

If you would like help in your native tongue, you may try a [LOCO sub-forum]("https://ubuntuforums.org/forumdisplay.php?f=183").  Be advised, however, that some of them are barely active and others have been dead for years.

---

