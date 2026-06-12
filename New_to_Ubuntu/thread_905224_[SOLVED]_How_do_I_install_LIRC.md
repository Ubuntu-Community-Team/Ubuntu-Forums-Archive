---
title: "[SOLVED] How do I install LIRC?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by vasiauvi on 2008-08-30
Hello,
I have updated from 7.10 to 8.04 with the hope that my remote control will finaly work.I read on forum and in other places how can I configure and make to work the remote control with lirc.But nothing worked.
I have a tv tunner WINFAST TV2000 XP and use Kdetv.
When i put in terminal: irrecord -H dev/input -d /dev/input/event6 /tmp/my-remote 
this is what I get: 
   irrecord -  application for recording IR-codes for usage with lirc

   Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

   irrecord: initializing '/dev/input/event6'
   irrecord: unable to open '/dev/input/event6'
   irrecord: could not init hardware (lircd running ? --> close it,  check  permissions).
Can anyone help me to configure the lirc?
Sorry, i know that are a lot of web pages and a lot of threats on this forum, I have read it bu nothing works.
Because of this problem i use also the WinXP and I want to skip from it.
Thanks!!

---

### Post by vasiauvi on 2008-08-30
I have tried this: [http://ubuntuforums.org/showthread.php?t=742129&highlight=remote+controller](http://ubuntuforums.org/showthread.php?t=742129&highlight=remote+controller) 
When I try to save the file hardware.conf after i've put the "lirc_dev lirc_i2c" on Modules section it tell me that I don't have the permision. :(  and when I type :
sudo modprobe lirc_i2c 
apears:
sudo: unable to resolve host vasia-home.:confused:

---

### Post by Ryadt on 2008-08-30
Post the output of:```
cat /etc/hosts
```

---

### Post by vasiauvi on 2008-08-30
I have managed to resolve the host problem.
I have used the gksudo gedit /etc/hosts   command.
But I don't manage to make LIRC work.It's very frustrating :((

---

### Post by Ryadt on 2008-08-30
> **vasiauvi said:**
> I have managed to resolve the host problem.
I have used the gksudo gedit /etc/hosts   command.
But I don't manage to make LIRC work.It's very frustrating :((

Try updating first```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by vasiauvi on 2008-08-30
> **Ryadt said:**
> Try updating first```
sudo apt-get update && sudo apt-get upgrade
```
I have updated and still doesn't work!!!

---

### Post by vasiauvi on 2008-08-30
When i write in the terminal : ```
cat /proc/bus/input/devices
```
This is the result:
```
I: Bus=0001 Vendor=107d Product=6609 Version=0001
N: Name="bttv IR (card=34)"
P: Phys=pci-0000:00:0a.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:0a.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010000 190 4801 1e0000 4400 100000 10000ffc
```

---

### Post by vasiauvi on 2008-08-31
It seems that I have resolved the problem with the help of this link:
[http://web.missouri.edu/~datcnc/leadtek_lirc_feisty.html](http://web.missouri.edu/~datcnc/leadtek_lirc_feisty.html)

---

