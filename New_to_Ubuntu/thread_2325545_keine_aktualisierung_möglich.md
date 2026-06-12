---
title: "keine aktualisierung möglich"
date: 2016-05-23
forum: New to Ubuntu
---

### Post by deddy-h on 2016-05-23
Konnte Sperre /var/lib/apt/lists/lock nicht bekommen - open (11: Die Ressource ist zur Zeit nicht verfügbar)
was kann man tun

---

### Post by mörgæs on 2016-05-23
Hi, welcome to the fora.

Please reboot the computer, close all applications which might open, run ```
sudo apt-get update
``` and post the output in CODE tags.

---

### Post by QIII on 2016-05-23
Please translate your inquiry into English and use English to conduct the rest of your thread.

This is an English-speaking forum.  Although I am perfectly happy to provide assistance in German elsewhere, I will not do so here.

---

### Post by Impavidus on 2016-05-23
That indicates that either there is another instance of a package manager front-end running or it didn't terminate cleanly. Maybe upgrades were being installed automatically? Close all instances of the package manager and reboot to make sure none are running. If you're absolutely positive the package manager doesn't run, you can manually release the lock.

Although I've no problem reading german, this is an english-language forum, so please use english. Else many users will be unable to help or benefit to solve their own problem.

---

