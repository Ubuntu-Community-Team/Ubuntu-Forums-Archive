---
title: "J2EE/bluetooth question"
date: 2007-02-07
forum: Programming Talk
---

### Post by docetes on 2007-02-07
hey,

does anyone know if I can code up a program to access my Bluetooth dongle using J2EE? I want to get a chat program up and running so my laptop and PDA can talk to each other ;)

thanks for the help,
Dave

---

### Post by docetes on 2007-02-07
or j2se

---

### Post by jblebrun on 2007-02-07
JSR-82 is the Java specification request dealing with Bluetooth APIs. Most implementationsn are for J2ME-capable devices. Here's a desktop implementation of JSR-82, although I haven't used it:

[http://www.avetana-gmbh.de/avetana-gmbh/produkte/jsr82.eng.xml](http://www.avetana-gmbh.de/avetana-gmbh/produkte/jsr82.eng.xml)

---

