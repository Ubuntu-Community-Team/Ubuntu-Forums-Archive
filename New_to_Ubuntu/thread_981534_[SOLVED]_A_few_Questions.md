---
title: "[SOLVED] A few Questions"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by yurikoster1 on 2008-11-13
Hey guys,

i know that MacOs uses afp and that windows uses smb. witch protocol does ubuntu use to connect to another ubuntu? and is there a way to make windows and mac computer automatically find a ubuntu computer attached to their network?

is there an esy way to download an application deb file and its dependencies for intall in a computer that is not connected to a network?

tnks in advance,
yuri

---

### Post by nhasian on 2008-11-13
in ubuntu just right click on whatever folder you want to share and then click *sharing options* i think it will prompt you to install samba if its not already installed.  then both windows and mac computers will be able to see the shared folder.

---

### Post by yurikoster1 on 2008-11-13
> **nhasian said:**
> in ubuntu just right click on whatever folder you want to share and then click *sharing options* i think it will prompt you to install samba if its not already installed.  then both windows and mac computers will be able to see the shared folder.

thanks 4 the info :)

---

### Post by quimico69 on 2008-11-13
Well, it depends on what you want to do.  If you only want to transfer files, there is sftp.  If you want to interact through a command line, you can use ssh.  If what you need is to read/write files on another system, there is NFS; and if you want to broadcast information that has to be available on all the nodes of a network, there is NIS.

Regarding your second question, yes, you can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and look for the packages you need, download them to a removable storage (e.g., USB stick) and put them on the machine that is off the net.  It is easy, but it can get very tedious, because you have to ensure that you have all the packages for all the dependencies.  The description of the package will tell you the required dependencies and some other that are recommended.  You can skip the recommended packages.

---

### Post by yurikoster1 on 2008-11-13
> **quimico69 said:**
> Well, it depends on what you want to do.  If you only want to transfer files, there is sftp.  If you want to interact through a command line, you can use ssh.  If what you need is to read/write files on another system, there is NFS; and if you want to broadcast information that has to be available on all the nodes of a network, there is NIS.

Tnks i was just curious :) ill kepp this informatin in mind :D

> **quimico69 said:**
> Regarding your second question, yes, you can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and look for the packages you need, download them to a removable storage (e.g., USB stick) and put them on the machine that is off the net.  It is easy, but it can get very tedious, because you have to ensure that you have all the packages for all the dependencies.  The description of the package will tell you the required dependencies and some other that are recommended.  You can skip the recommended packages.

thats the way i was doing it :P. i was hoping 4 an apt-get like command but nothing is perfect :) tnks again,
yuri

---

### Post by quimico69 on 2008-11-14
glad to help.

---

