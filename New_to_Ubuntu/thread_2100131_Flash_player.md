---
title: "Flash player"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by Mike Zahorik on 2012-12-31
I just downloaded flash player and I can see that the files are there, but how do you install it? Is there an exe file that needs to be started?

Mike

---

### Post by MichaelGld on 2012-12-31
Where did you download it from? I would recommend going through the Software Center. Just search for the program, click install, then your password. Exe files are Windows files.

---

### Post by mamamia88 on 2012-12-31
> **MichaelGld said:**
> Where did you download it from? I would recommend going through the Software Center. Just search for the program, click install, then your password. Exe files are Windows files.

adobe flash player is no longer supported in linux.  if you want to use it i would highly reccomend google chrome which has it's own version built in.   you can't install exe files in ubuntu by default and if you did it wouldn't work for a native linux browser anyway.    exe is a windows executable file so they won't work on linux without running wine which is a program that lets you run windows programs.   that being said you can probably still get flash in the ubuntu repos.  not quite sure since i don't use ubuntu anymore

---

### Post by Mike Zahorik on 2012-12-31
I was using Google maps and I was told that I needed flash to continue a[SIZE=3]nd it provided a link, so..... I down loaded it. Got a bunch of files, but now I need to know how to get it going.

Mike

---

### Post by mamamia88 on 2012-12-31
> **Mike Zahorik said:**
> I was using Google maps and I was told that I needed flash to continue a[SIZE=3]nd it provided a link, so..... I down loaded it. Got a bunch of files, but now I need to know how to get it going.

Mike
you got tricked into downloading something you didn't need.      you shouldn't need flash for google maps. if you want flash download the google chrome and install it.  adobe has discontinued flash for linux but google still includes it in their browser.

---

### Post by Mike Zahorik on 2012-12-31
Thanks, not first time I've been in the barrel. But.... in windows exe are executable files, what are executable files in ubuntu?

Mike

---

### Post by mamamia88 on 2012-12-31
> **Mike Zahorik said:**
> Thanks, not first time I've been in the barrel. But.... in windows exe are executable files, what are executable files in ubuntu?

Mike

well anything anything with a .bin,.sh.or .deb.  .sh is a shell script which runs in a terminal, .bin stands for binary, and .deb is a debian package like an exe.  just avoid running anything without knowing what it is for now on.  software in ubuntu is installed in a different way.  you shouldn't have to download executable files and manually run them.  if you want to install something search synaptic or software centre and in rare cases add a ppa to the system

---

### Post by Mike Zahorik on 2012-12-31
I'm still in a windows mentality and very green when it comes to Ubuntu. Thanks for the help.

Mike

---

### Post by mamamia88 on 2012-12-31
> **Mike Zahorik said:**
> I'm still in a windows mentality and very green when it comes to Ubuntu. Thanks for the help.

Mike

well good thing you were on linux.  sure fire way to get a virus is to go downloading executables from random sources and running them.  if something tells you you need flash in windows be sure to download it directly from adobes website.  clicking one of those links is basically like handing over your keys to a robber.

---

### Post by pqwoerituytrueiwoq on 2012-12-31
```
sudo sed -i 's/\# deb h/deb h/;s/\# deb-src h/deb-src h/' /etc/apt/sources.list;sudo apt-get update;sudo apt-get install adobe-flashplugin adobe-flash-properties-gtk

```
running that in a terminal will give you Adobe flash just like you would get it from adobe's site
a deb file is for installing software

---

