---
title: "Qjackctl forces quit on startup Ubuntu 11.10 Beta 1"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by shaneo1 on 2011-09-12
After running a some little run of the mill updates today I am unable to start Qjackctl, well it starts then forces quit on me. Here is the info from a terminal start:

```
shane@shane-Aspire-8930:~$ qjackctl

(qjackctl.real:2660): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(qjackctl.real:2660): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(qjackctl.real:2660): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(qjackctl.real:2660): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Warning: no translation found for 'en_US' locale: /usr/share/qt4/translations/qt_en_US.qm
Warning: no translation found for 'en_US' locale: /usr/share/locale/qjackctl_en_US.qm
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-e0VvN5vVnm,guid=d9428c74c3e998e08729610800000021" 
Registered DEC:  true 

```Any clued up people out there able to assist me please.  I a complete cluts when it comes to anything to do with Jackd.  But I has been working yesterday :) :guitar:
I have even sudo apt-get purge qjackctl and reinstalled it, removed all the files by sudo su root access and reinstalled, just not sure where to go now :( 

Cheers in advance techy peeps.

---

### Post by shaneo1 on 2011-09-14
Is anybody else having qjackctl locking up on them when the application is opened. Not able to use it have to use have is very terminal.  Any help would. Be great.

---

### Post by Elfy on 2011-09-14
Thread moved to Ubuntu +1 (Oneiric Ocelot).

---

### Post by cariboo on 2011-09-14
It seems like there are dependency problems with qjackctl, I'd suggest filling out a bug report on your problem. See screenshot.

---

