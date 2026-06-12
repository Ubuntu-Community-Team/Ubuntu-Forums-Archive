---
title: "Problem when packaging my app (dh_make missing file)"
date: 2012-11-13
forum: Packaging and Compiling Programs
---

### Post by FSMaximeH on 2012-11-13
Hello Folks

I am trying to package one of my own shared-library on my own PPA since more than a week now, but I do not succeed. It is the first time I try to put somehting on my launchpad and I can't get it even after googling a lot.

Currently it fails when I try to compile it with
```
sudo pbuilder build *.dsc 
```It says
```
dh_install: libcopy-playlist-backend-dev missing files (usr/include/*), aborting

```The whole log for this command is here [http://pastebin.com/4Tf5fy6d](http://pastebin.com/4Tf5fy6d)

Any help or explanation  is welcome!!

I am following this tutorial: [http://doc.ubuntu-fr.org/tutoriel/creer_un_paquet#creation_du_paquet_source](http://doc.ubuntu-fr.org/tutoriel/creer_un_paquet#creation_du_paquet_source)

_Here under are the files I am using:_

Copyright                                                         [http://pastebin.com/qmnTQMWt](http://pastebin.com/qmnTQMWt)
Control                                                               [http://pastebin.com/qabx8zj2](http://pastebin.com/qabx8zj2)
Changelog                                                     [http://pastebin.com/SzwuEZKt](http://pastebin.com/SzwuEZKt)
CMakeLists.txt                                                [http://pastebin.com/6KsAUenC](http://pastebin.com/6KsAUenC)

libcopy-playlist-backend-dev.dirs           [http://pastebin.com/VkykBPbm](http://pastebin.com/VkykBPbm)
libcopy-playlist-backend-dev.install     [http://pastebin.com/1pw7d5Jk](http://pastebin.com/1pw7d5Jk)
libcopy-playlist-backend.dirs                        [http://pastebin.com/xnbac02R](http://pastebin.com/xnbac02R)
libcopy-playlist-backend.install               [http://pastebin.com/DPruXApT](http://pastebin.com/DPruXApT)

---

### Post by FSMaximeH on 2012-11-14
Upping ?*

---

### Post by FSMaximeH on 2012-11-16
"Re-Up"  
   - [SIZE=1]*Eminem*[/SIZE]

---

