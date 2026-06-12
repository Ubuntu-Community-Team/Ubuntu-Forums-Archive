---
title: "Easiest way to add/remove desktop environments"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by husnos on 2012-03-26
1) Install tasksel

sudo -i

apt-get install tasksel


2) Run tasksel by typing tasksel while in sudo


3) Select/unselect desktop envrionments

---

### Post by Kevin McCready on 2012-03-26
From the project page
[https://help.ubuntu.com/community/Tasksel]("https://help.ubuntu.com/community/Tasksel")

"WARNING: Use tasksel only to install tasks, never to remove any! According to [https://launchpad.net/bugs/574287](https://launchpad.net/bugs/574287) it will remove each package in the list of that task (and possibly render your system unusable)."

"Because the package managers now have most of the tasks as meta-packages, tasksel is not installed by default on editions of Ubuntu (such as Desktop editions) that have package managers."

---

### Post by collisionystm on 2012-03-26
I have used tasksel too. Things I have learned:

If you are running something that's not pure Ubuntu. I.E. Mint, Zentyal...etc. Don't use it.

2nd. Like stated, do not use it to remove to desktop environment unless you want your system back to stock. Meaning it will remove all programs you have installed and put only the original ones that came with Lubuntu, Kubuntu, Ubuntu.

Just use

sudo apt-get install kubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install ubuntu-desktop

to remove...

sudo apt-get purge ubuntu-desktop
sudo apt-get purge kubuntu-desktop ....etc.

When you install the -desktop metapackage it comes out much nicer than just doing something like sudo apt-get install kde4 or sudo apt-get install lxde

If you don't like the boot splash that you get... I.E. you are now seeing a kubuntu bootsplash instead of the nice Purple ubuntu, you just install the plymouth kubuntu theme from software center. There is also a file to change without the need to install... but to be honest I am on a Windows Computer right now :p

---

### Post by husnos on 2012-03-26
i don't know. it worked fine for me on ubuntu.

---

### Post by collisionystm on 2012-03-26
> **husnos said:**
> i don't know. it worked fine for me on ubuntu.

Just saying.. Next time you do it...pay attention to what its removing.

---

### Post by Kevin McCready on 2012-03-26
> **collisionystm said:**
> 
sudo apt-get install kubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install ubuntu-desktop


Do any of these NOT use PCManFM? Is there a quick way of finding out?

---

### Post by husnos on 2012-03-27
> **collisionystm said:**
> Just saying.. Next time you do it...pay attention to what its removing.

yeah sure. maybe i got lucky. thanks anyway.

---

### Post by MG&amp;TL on 2012-03-27
> **Kevin McCready said:**
> Do any of these NOT use PCManFM? Is there a quick way of finding out?

```
apt-cache depends <package>
```

gives the dependencies of a package.

Only lubuntu-desktop uses PCManFM. What's the problem with it?

---

