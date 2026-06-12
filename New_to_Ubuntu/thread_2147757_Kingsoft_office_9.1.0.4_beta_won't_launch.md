---
title: "Kingsoft office 9.1.0.4 beta won't launch"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-05-23
Hi, I have Ubuntu 13.04 installed and tried to install Kingsoft office (9.1.0.4 - beta), but when I launch it (from menu) nothing happens..

Thanks for any help..

---

### Post by monkeybrain2012 on 2013-05-23
try to launch it in the terminal and see the output. The command is probably just 'kingsoft' (no quotations)

---

### Post by ViliX64 on 2013-05-23
Tried that, but can not find the command (kingsoft does not work, neither kingsoft-writer)

---

### Post by dino99 on 2013-05-23
[http://linuxg.net/how-to-install-wps-office-kingsoft-office-on-ubuntu-and-fedora/](http://linuxg.net/how-to-install-wps-office-kingsoft-office-on-ubuntu-and-fedora/)

---

### Post by dino99 on 2013-05-23
oops, dupe

---

### Post by ViliX64 on 2013-05-23
Well, I don't have problems installing it.. I have problems running it..

---

### Post by joyblaze on 2013-05-23
I too have the problems in installing "kingsoft-office_9.1.0.4032~a10_i386.deb", i have downloaded this from softpedia.com, and copied this to machine. And when i opened this using software center, the installation progress bar stops in middle and comes back.

---

### Post by ViliX64 on 2013-05-23
Well, I installed it through terminal and it created launchers, etc.. but still can not launch..

---

### Post by cbcollins on 2013-07-12
I also ran into this problem, installed it from the terminal and had the launchers but they didnt do anything when clicked. I believe the problem was that Im on a 64 bit OS. Everything works now that I have installed the package[FONT=verdana, arial, sans-serif][COLOR=#333333] ia32-libs. [/COLOR][/FONT][FONT=verdana, arial, sans-serif][COLOR=#333333]

```
[/COLOR][/FONT][COLOR=#333333][FONT=verdana]sudo apt-get install ia32-libs
[/FONT][/COLOR][FONT=verdana, arial, sans-serif][COLOR=#333333]
```

then install your kingsoft version and it should work[/COLOR][/FONT]

---

