---
title: "Samba on Ubuntu"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by shoaibi on 2008-05-08
I installed something called "Samba" from Add/Remove on 8.04. now whenever i try to run that, it crashes... why?

Plus there are some files on my system that even root cant change permissions of... what should i do?

---

### Post by njparton on 2008-05-08
Samba is a program that allows you to share your linux partitions with windows computers over your network.  If you don't need it, remove it:
 
```
 
sudo apt-get remove samba

```
 
I've found it very stable though so you have other underlying problems by the sound of it.

---

### Post by Rocket2DMn on 2008-05-08
Samba runs as a service on your system, you can stop/start/restart it with
```
sudo /etc/init.d/samba start|stop|restart
```
It is used to share files and printers with windows computers.  More here - [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Dani Filth on 2008-05-08
If you were refering to how to use Samba, I think you execute it the wrong way. If you simply enter "samba" in the terminal, it would say "bad command" or something. 
As far as I know, to use Samba, you open Nautilus, press Ctrl+L, type in "smb://The-remote-LAN-IP-you-want-to-access" e.g "smb://192.168.111.11".

I don't know much about files' permission, though.

---

