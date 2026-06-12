---
title: "What to do about updatling to newer Ubuntu?"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by kriket on 2012-11-25
I am running Ubuntu 10.04 LTS, on an old IBM Think Pad T40.

Thought it was time to try latest LTS version of Ubuntu, but got 'This Kernel requires the following features not present on the CPU:*** pae***'

Having searched the forums I am not sure what my best option is/or I have understood all I have read;
1 Skip 12:04 LTS and go for 12:10
2 Install Alt version
3 Try Lubuntu (which is not LTS either)
4 Stick with what I have

The computer is old but works, but have to burn discs to install, and do not want to end up with loads of discs that do not work for me

---

### Post by Paqman on 2012-11-25
> **kriket said:**
> 
1 Skip 12:04 LTS and go for 12:10
2 Install Alt version
3 Try Lubuntu (which is not LTS either)


This won't help. All newer versions of Ubuntu install the PAE kernel by default. PAE lets 32-bit machines use 4GB+ of RAM, so it's generally a good thing.

> 4 Stick with what I have

There are non-PAE kernels in the 12.04 repositories, but it looks like the upgrade process is not letting you pick one. If you try reinstalling from scratch using a 12.04 disk it might install a non-PAE kernel for you.

---

### Post by Cheesemill on 2012-11-25
Or you can use the non-pae Mini CD to do an installation of 12.04.

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/mini.iso](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/mini.iso)

---

### Post by monkeybrain2012 on 2012-11-25
I read somewhere on the forum that Lubuntu uses non pae, may be someone can confirm it. It works a lot better on old machine. It is not LTS, but if you have a separate /home partition updating shouldn't be too much trouble.

---

### Post by kriket on 2012-11-25
Thank you both for quick replys.

Think I will give the non-pae Mini CD to do an installation of 12.04. ago.

---

### Post by MG&amp;TL on 2012-11-25
> **monkeybrain2012 said:**
> I read somewhere on the forum that Lubuntu uses non pae, may be someone can confirm it. It works a lot better on old machine. It is not LTS, but if you have a separate /home partition updating shouldn't be too much trouble.

It doesn't, sorry. Much as I'd believe Lubuntu would like to, we just don't have the manpower to maintain a separate tree.

---

### Post by Paqman on 2012-11-25
> **kriket said:**
> Thank you both for quick replys.

Think I will give the non-pae Mini CD to do an installation of 12.04. ago.

Just so you know, the mini.iso installs a command-line system by default. Once it's installed you should enter the command:
```
sudo tasksel
```
and you'll be able to pick which kind of system you want to install.

---

