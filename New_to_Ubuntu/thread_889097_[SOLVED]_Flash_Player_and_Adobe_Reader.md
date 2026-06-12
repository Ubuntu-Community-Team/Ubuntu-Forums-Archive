---
title: "[SOLVED] Flash Player and Adobe Reader"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-13
How do I get Flash Player and Adobe Reader installed onto my machine? I've went to adobe.com and downloaded the .rpm files but they won't run.

---

### Post by alienexplorers on 2008-08-13
You need to convert an RPM to deb file using the program ALIEN;
> sudo alien -d nameofprogram.rpm

It would be a lot easier if you downloaded the tar.gz or tar.bz2 file.
The easiest would be a deb file which does not need any special help.

---

### Post by dje on 2008-08-13
rpm packages are for red hat distros and do not work on debian based distros (well they can be converted but this is not the best way to do it)
for flash player run in a terminal (applications >> accessories >> terminal):
```
sudo apt-get install flashplugin-nonfree
```
for acrobat reader, follow the instructions [here]("http://www.ubuntu1501.com/2008/04/medibuntu-for-hardy-heron.html") to add the medibuntu repo then do the following in a terminal:
```
sudo apt-get install acroread
```

dje

---

### Post by ArturoSan on 2008-08-13
Same problem here with 8.o4lts. Error msg said the installer does not support 64 bit systems. ALSO you need TAR version NOT RPM, I believe.

---

### Post by dje on 2008-08-13
> **alienexplorers said:**
> You need to convert an RPM to deb file using the program ALIEN;

when there are deb packages available it isnt recommended to do this ;)

dje

---

