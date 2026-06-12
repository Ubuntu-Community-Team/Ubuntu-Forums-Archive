---
title: "Start in command line, LILO"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by suspendido9veces on 2013-05-21
Hello friends, I am new user of Lubuntu (13.04), I have 2 questions 
1) how do I start lubuntu not start the graphic mode??? I want to start in command line.
2) It is possible to install LILO instead of Grub2??? thanks:P

---

### Post by linuxtechguy on 2013-05-21
1. [http://askubuntu.com/questions/86483/how-can-i-see-or-change-default-run-level](http://askubuntu.com/questions/86483/how-can-i-see-or-change-default-run-level)
2. Lilo is extremely old and outdated. Why dont you want to use grub?

---

### Post by oldos2er on 2013-05-21
> **suspendido9veces said:**
> Hello friends, I am new user of Lubuntu (13.04), I have 2 questions 
1) how do I start lubuntu not start the graphic mode??? I want to start in command line.
:P

In terminal, run ```
cd /etc/default/

sudo cp grub grub.backup

sudo nano grub
``` Change the line 

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to "GRUB_CMDLINE_LINUX_DEFAULT="text"

Save your changes and exit nano with Ctrl-O, Ctrl-X. Run ```
sudo update-grub
``` Reboot.

---

### Post by suspendido9veces on 2013-05-21
Many thanks !!:P

---

