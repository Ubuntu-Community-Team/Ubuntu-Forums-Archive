---
title: "Need one thing thats all."
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Solais on 2008-09-13
Hey guys, I'm really new to Linux and stuff, got bored of xp and wanted to try something new. So my cousin gave me a live cd, I installed and updated it. I put all my music files pictures and setups and such. Im a huge MMO fan, so I play alout of mmo's like: World of Warcraft, Ragnarok Online, Lineage 2 and others. I was told I can install and play wow by getting a program called wine, I went to winehq.com download the 1.0 version and extracted it. Um, I did not understand at all the read me, but I saw my cousin do it once in his pc with the Terminal, may anyone help me install this? like the command and such :):confused:

---

### Post by ChanServ on 2008-09-13
open up the terminal and do:  

```
sudo apt-get install wine
```

it is usualy better to install programs from the repos, becasue they will be better supported and you will get automatic updates

EDIT: this may also help with getting WoW to work in wine [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

### Post by swoll1980 on 2008-09-13
easiest way to install wine is to
```
sudo apt-get install wine
```

---

### Post by Solais on 2008-09-13
Cool ^^ I see it installing, btw, before I left xp i went to program files and got my wow ro and lineage folder, I can just drag and drop them in the program files of wine yes?:confused:

---

### Post by ChanServ on 2008-09-13
> **Solais said:**
> Cool ^^ I see it installing, btw, before I left xp i went to program files and got my wow ro and lineage folder, I can just drag and drop them in the program files of wine yes?:confused:

yep, wine creates it's own c:// drive

---

### Post by Solais on 2008-09-13
> **ChanServ said:**
> open up the terminal and do:  

```
sudo apt-get install wine
```

it is usualy better to install programs from the repos, becasue they will be better supported and you will get automatic updates

EDIT: this may also help with getting WoW to work in wine [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

repos?:confused:

---

### Post by Tatty on 2008-09-13
You can install the version of wine in the Ubuntu repos via Applications->Add/Remove.

However, this is not the latest version of wine, if you want to install the latest version of wine then you need to add the semi-official wine ubuntu repo via these instructions:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)


You might also want to check out the official documentation of installing software in Ubuntu.  Its not often that you download an installer from a website then just click and run it.

[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

If youre new to linux in general then you should probably read through all of that guide.


EDIT: Repos is short for repositories - which are basically big servers which hold thousands of pieces of software.  Installing directly from these is the normal way to install software in linux.

---

### Post by ChanServ on 2008-09-13
> **Solais said:**
> repos?:confused:

ubuntu reposatories, were most (if all) ubuntu packages are stored, this make sit easy to upgrade and install software :D

---

### Post by Solais on 2008-09-13
Thanks alot everyone :)

---

### Post by SunnyRabbiera on 2008-09-13
Just remember wine still isnt 100% with games, but it seems to get better every time.

---

