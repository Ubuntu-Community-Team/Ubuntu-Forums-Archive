---
title: "what flash player"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by westentertainer on 2008-05-28
hello at long last i have ubuntu working booting with vista  xp  can someone tell me what flash player do i need for watching tou tube etc,, iv downloaded a couple but it states they are not supported i have ubuntu 7.10   oh i am downloadeing updates at the moment   it states ther is an update to 8,04 should i    thank you in advance

---

### Post by FuturePilot on 2008-05-28
Copy and paste this into a terminal
```
sudo apt-get install flashplugin-nonfree
```
That will install the Adobe Flash Player.

---

### Post by westentertainer on 2008-05-28
ok im new to ubuntu  were will i find ;terminal; thank you

---

### Post by sayakb on 2008-05-28
Applications->Accessories->Terminal

---

### Post by dje on 2008-05-28
Applications >> Accessories >> Terminal

hope that helps,
dje

EDIT: posted at the same time :)

---

### Post by westentertainer on 2008-05-28
tony@tony-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for tony:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tony@tony-desktop:~$ sudo apt-get install flashplugin-nonfree
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tony@tony-desktop:~$ 
this is what i get

---

### Post by dje on 2008-05-28
You must wait for the updates to finish because the updates are using the apt package manager and you are trying to install using the apt package manager, you can only do one thing with it at a time

dje

---

### Post by FuturePilot on 2008-05-28
wait until your updates are done installing.

---

### Post by westentertainer on 2008-05-28
hey it works well i must say something i have been a member of different forums for many years but i have never had help so quickly as this forum  many thanks

---

### Post by Hozza on 2008-05-28
if you upgrade to hardy heron, all of the new repository's which will have new flash player updates

---

