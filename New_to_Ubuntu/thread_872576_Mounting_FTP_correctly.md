---
title: "Mounting FTP correctly"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by JeppeM on 2008-07-28
Hey all...

I'm a webmaster, and i use ftp on a daily basis, so getting this fixed would really help me a lot. I once read a tutorial on how to mount FTP, but that was a long time ago, and since then i totally forgot what i did (great, eh?). But anyway, when i boot my computer, i have the mounted FTP as a folder in my Places menu, but when i open a file from there using gedit, change it and then want to save it again, it first says that it cannot make a backup file, and then it says that it cant save the file cause it doesn't exists. All i end up with is a 0 byte file on the server, as if it totally wiped the file :(

So what i need help with is the following:

1) where could i have placed the command to mount the FTP at startup? 
- I checked /etc/fstab, and there's nothing there.

2) How can i mount it correctly, such that it behaves like you would expect from a normal "drive" (ie, save correctly with gedit)?

---

### Post by Cypher on 2008-07-28
Mount FTP? Are you certain your remembering correctly? FTP, which literally stands for File Transfer Protocol, is a scheme of transefering a file from one machine to another either through the command line or through a GUI-driven program..but this is usually not a persistent connection.

Protocols such as NFS/Samba allow you mount partitions from other machines locally and use them as a local filesystem.

---

### Post by stevoo on 2008-07-28
most probably youll need to run a script, create one and make it run on login to open the terminal and connect dirrectly to the ftp that you want.

No way to mount an ftp other than that.

---

### Post by Bachstelze on 2008-07-28
> **stevoo said:**
> No way to mount an ftp other than that.

[http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/)

---

### Post by mia.king on 2008-12-01
In Ubuntu 8.10 use 
Places - Connect to server...

If it works (doesn't for the site I want to use) is the easiest.

---

