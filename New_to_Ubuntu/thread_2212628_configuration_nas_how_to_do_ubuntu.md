---
title: "configuration nas how to do ubuntu"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by landwim4 on 2014-03-22
hi how can i install nas buffalo **LS-WX2.0TL/R1-EU** with ubuntu 12.04 this nas is build for windows and mac osx can someone help me its very diffulcult for me (beginner pfffff)

---

### Post by Ubi_one_2014 on 2014-03-22
you want to install ubuntu 12.04 on it?

---

### Post by landwim4 on 2014-03-22
no i want to share it

---

### Post by Ubi_one_2014 on 2014-03-22
assuming it has samba installed,

mount -t cifs -o username=share,password=psswd,uid=your_username //192.168.178.11/MP3 /path/to/dir/in/dolphin

the username and paswd are a user that exists on the nas, so user share, on the nas must have access to the //192.168.178.11/MP3 dir.
u can obtain this by loging in into the nas webinterface, and create a user, and assign access
the iud= means your username on ubuntu
the //192.168.178.11/MP3 is the path to your MP3 files, wher the ip is the ip of the nas
the /path/to/dir/in/dolphin is a local directory created to linked to the NAS

an example , in your case, can be:
mount -t cifs -o username=share,password=ubuntu,uid=landwim4 //192.168.178.11/MP3 /home/landwim4/music

othwerise you can add en entry in dolphin, where u have to use :
smb://IP_of_NAS as the location

the first option works for me, and works like it did in windows.
so i can read/write/delete files and folders by using dolhin

the second option does work, but read/write and delete not, it only shows the NAS

---

