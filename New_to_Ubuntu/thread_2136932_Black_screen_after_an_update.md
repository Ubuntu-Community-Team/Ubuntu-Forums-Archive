---
title: "Black screen after an update"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by BobosAbelMihai on 2013-04-19
Hello everybody, yesterday i updated my ubuntu 12.10 with these updates:
> *Important security updates:
1.Common files used by various X servers(xserver-common)
2.Xorg X server-core server(xserver-xorg-core)

*Other updates(LP-PPA-webupd8team-java)
1.Oracle Java(TM) Development kit (JDK) 7 (oracle-java7-installer)
2.Oracle JDK7 Installer meta package(oracle-JDK7-installer)

Today i started my laptop and after grub all i get is a back or a purple screen(purple with ubuntu loading bar) and freezes this way. Nothing happens.

Please help me, because i don't want to reinstall the OS again.

Thank you

---

### Post by BobosAbelMihai on 2013-04-19
Nobody? Just tell me if there is nothing I can do, and I will reinstall the OS.

---

### Post by tejodite on 2013-04-19
i have the same problem today and i just fixed, but first do you use a AMD graphic card?

---

### Post by tejodite on 2013-04-19
well anyways what i do was: get into recovery mode in the grub, then i when to the root user and use this command ¨sudo sh /usr/share/ati/fglrx-uninstall.sh¨ this restart the enviroment configuration of the drivers to the org.x so when the sistem restart i just re-activate the ATI drivers and now everything is fine again

---

### Post by BobosAbelMihai on 2013-04-19
Well, now i just finished my new install....
I installed again everything.

Thank's a lot anyway ;)

---

