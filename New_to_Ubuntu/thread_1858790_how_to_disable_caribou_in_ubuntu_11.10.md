---
title: "how to disable caribou in ubuntu 11.10"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-10-13
in 11.10 every time i log in i get the popup message to enable caribou. how to i stop this. i cant find in the startup programs.

---

### Post by spybee on 2011-10-19
I suppose you have to delete the desktop entry at /etc/xdg/autostart 
You can use the following command in the terminal: 

gksu nautilus /etc/xdg/autostart

Since Ubuntu 11.10 not all startup applications are shown in the GUI application.

---

### Post by rburkartjo on 2011-10-19
spy tks

---

### Post by kalimojo on 2011-10-26
> **rburkartjo said:**
> spy tks

can you expand on that, are you saying its spyware ?

---

### Post by rburkartjo on 2011-10-26
kal it is not spyware it is just a program that i dont want to startup when i log in

---

### Post by Arny006 on 2011-12-02
I don't like this search in the system-files which one is reserved only to old linux-users!

It's much more easy to press "Alt+F2" and copy/paste "gnome-session-properties".

That will start your "Autostart Application Manager". You can disable the autostart by clicking or delete it completely also as linux newbe.

I don't understand why many people make simple things complicated.

---

### Post by M3TA4 on 2012-04-05
arny.. like spybee said there is alot of program missing in there. And command-line will be around for a long time. Because it is alot easier to explain. And in most cases easier to do so. Also if you run into a problem when using terminal. You can check the log for errors. alt+f2 can disable if you are running compiz. In fact; alt+f2 tend to bug out alot.

thanx alot spybee for the easy fix to the solution.

---

