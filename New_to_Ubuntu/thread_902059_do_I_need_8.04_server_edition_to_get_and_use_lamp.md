---
title: "do I need 8.04 server edition to get and use lamp"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by krahsh dummay on 2008-08-27
I have read threads on lamp and dont understand

do I have to  run a headless Ubuntu8.04 server edition to use lamp and access it remotely ? 

Orr can i just sudo apt get the lamp pkg and run them out of plain ubuntu 8.04 gui ?

i got a feelin this is a dumb question but after all i've read I still don't understand how and where to put lamp

I would really like to learn how to make web pages with php and how to use Mysql as a data base for the web page material. 

thanks for the time

---

### Post by perlluver on 2008-08-27
You can install Lamp in Ubuntu 8.04 with a GUI.  Although it isn't recommended, because it is safer to run it without a GUI.  To install the LAMP server in Ubuntu, with a GUI, type this in a terminal.

```
sudo tasksel install lamp-server
```

---

### Post by jerome1232 on 2008-08-27
You don't have to install server edition to get a lamp setup, although I prefer having a headless remotely administered server, you certainly can install it on a desktop with a gui.

I don't know if desktop version has tasksel but you should be able to use that to get a lamp server

```
sudo tasksel
```

---

### Post by nicedude on 2008-08-27
I am not sure but I searched in synaptic for you and don't find lamp anything and I am in regular Ubuntu Hardy so you may be right, but I am not sure but thought you might like my synaptic results none the less.

---

### Post by krahsh dummay on 2008-08-27
Thank you

---

### Post by krahsh dummay on 2008-08-27
thank you

---

### Post by krahsh dummay on 2008-08-27
newbi took me awhile to figure out how to say thanks

I guess its got to be a headless ubuntu server I just dont understand why its so hard for me to get that through my thick head. but I know that if I could figure out w95 ist edition I can get any thing.

---

### Post by perlluver on 2008-08-27
> **krahsh dummay said:**
> newbi took me awhile to figure out how to say thanks

I guess its got to be a headless ubuntu server I just dont understand why its so hard for me to get that through my thick head. but I know that if I could figure out w95 ist edition I can get any thing.

It doesn't have to be headless, I am running Gnome GUI, and a Lamp server, it is just safer to run it without a GUI.  If you are just learning, and are using it as a home server, you will be fine with a GUI.

---

