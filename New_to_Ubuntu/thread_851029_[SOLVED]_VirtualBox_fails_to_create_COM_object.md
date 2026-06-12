---
title: "[SOLVED] VirtualBox fails to create COM object"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by nuddernuby on 2008-07-06
I have just installed VirtualBox on 8.04 - carefully following SendDerek's How To.
When attempting to start the application from Applications>System Tools>innotek VirtualBox I get the following Error Message:

> Failed to create the VirtualBox COM object
Callee RC: 0x80470007


Any advice?

---

### Post by real.africa on 2008-07-06
Have you tried the new version (1.6.2) of Virtual Box available from Sun, who have taken over its developement?

---

### Post by real.africa on 2008-07-06
COM objects are part of the Microsoft windows O/S. It would seem you have a version of Virtualbox designed for MS Windows. Do you run that O/S as your main O/S with Ubuntu as a 'Guest O/S' in Virtualbox? If not, what is your configuration?

---

### Post by nuddernuby on 2008-07-06
Ubuntu 8.04 is the host system. I installed virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb
in order to load XP.
Should I attempt to get version 1.6.2?

---

### Post by nuddernuby on 2008-07-06
Version 1.6.2 installed - up and running.
Thank you for your advice, real.africa.

---

### Post by real.africa on 2008-07-06
You're most welcome! I'm just glad this noob was able to help in this instance:)

---

