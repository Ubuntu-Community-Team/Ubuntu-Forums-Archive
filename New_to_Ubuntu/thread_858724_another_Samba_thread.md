---
title: "another Samba thread"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by stalkier on 2008-07-13
Ok so I need to setup file sharing between 2 Ubuntu PCs. I have a network setup right now under windows. The PC both detect the windows PC but not each other. I know of Samba but do not know how to configure it etc. I DO have it installed oon both PC I believe. (at least I thought I did.) I did install the GUI and noticed that samba is installed already. 

Any suggestions will help.Thanks in advance. I have been learning a lot since I canned Windows on my desktop. I am still dual-booting my laptop for design purposes. (Using Adobe Master Suite CS3 :D)

Regards ~ John

---

### Post by bodhi.zazen on 2008-07-13
what are you trying to ed exactly ?

If you are sharing files, and you have 3 computers, which one is the server and which the clients ?

If you are wanting to use your Ubuntu boxes as clients, all should be working out of the box.

If you want one (or both) of the Ubuntu box(es) to act as servers as well, you need to install samba :

```
sudo apt-get install samba
```

[uwiki]ComprehensiveSambaGuide[/uwiki] 

 [uhelp]community/SettingUpSamba[/uhelp]

---

