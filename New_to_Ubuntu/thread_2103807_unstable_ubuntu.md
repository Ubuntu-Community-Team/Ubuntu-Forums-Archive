---
title: "unstable ubuntu?"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by damianos t on 2013-01-11
While trying to download drivers for my printer, the ubuntu screen becomes black and appears:
stopping mount network high system
starting crash report submission daemon
stoping system V run level compatibility
nouveau 0000 failed to idle channel 1, 2, 3 repeatedly

Is there a problem with my installation of ubuntu or ubuntu is just unstable?
No offence but it has problem even to download the drivers of the printer.

---

### Post by iMac71 on 2013-01-11
please give the following informations:
- what's your printer?
- what's the Ubuntu release you use?
Without them, it's very difficult to help you.

---

### Post by damianos t on 2013-01-11
hp laserjet 1522n
ubuntu 12.10

---

### Post by iMac71 on 2013-01-11
> **damianos t said:**
> hp laserjet 1522n
ubuntu 12.10try to download the driver from the following link:
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=it&prodNameId=3442751&prodTypeId=18972&prodSeriesId=3442750&swEnvOID=2020&taskId=135&swLang=8](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=it&prodNameId=3442751&prodTypeId=18972&prodSeriesId=3442750&swEnvOID=2020&taskId=135&swLang=8)

---

### Post by mörgæs on 2013-01-11
If the download itself (not the installation) gives problems there is something which needs to be looked at. Please give a complete hardware description.

---

### Post by audiomick on 2013-01-11
> **mörgæs said:**
>  Please give a complete hardware description.

Open a terminal and do
```
sudo lshw
```

Post the output here. The list is long, so use the # button at the top of the post window to put code tags around it.

---

### Post by damianos t on 2013-01-11
How can I open a terminal?

---

### Post by howefield on 2013-01-11
Keyboard shortcut is Ctrl+ALt+T or search the dash by pressing the Super (Windows) key and start typing terminal, the icon should appear within a few keystrokes.

---

### Post by mörgæs on 2013-01-11
> **audiomick said:**
> Open a terminal and do
```
sudo lshw
```

Post the output here. The list is long, so use the # button at the top of the post window to put code tags around it.


... or 
```
sudo lshw > lshw.txt
``` , which will direct the output to a file and not to the screen. Might take a few seconds to run.

---

### Post by audiomick on 2013-01-11
> **damianos t said:**
> How can I open a terminal?

Sorry, should have mentioned that. Thanks howefield. ;)

---

### Post by damianos t on 2013-01-14
...

---

### Post by coffeecat on 2013-01-14
@damianos t, you forgot this bit:

> **audiomick said:**
> The list is long, so use the # button at the top of the post window to put code tags around it.

I've added code tags for you because you also lose all formatting without them.

Good luck! :)

---

### Post by damianos t on 2013-01-14
Thanks! Let's hope that we will be able to detect if there is a trouble.

---

