---
title: "Dual boot help"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Sly-.- on 2008-05-02
Hi all, I wanted to try out the new ubuntu 8.04 but dual boot it with my XP. I've done this before, installing it in a seperate drive but now I want to split my first drive and install it there. Could anyone help me out or point me to the right direction of a tutorial or something. Cheers.

---

### Post by mlentink on 2008-05-02
> **Sly-.- said:**
> Could anyone help me out or point me to the right direction of a tutorial or something. Cheers.

[https://help.ubuntu.com/8.04/switching/index.html](https://help.ubuntu.com/8.04/switching/index.html)

---

### Post by elord on 2008-05-02
i try this installing two OS in one PC..All you have to do is    1st install the Windows Xp and install the Ubuntu in same partition..No need for you to separate in installing Two OS in two partion..


C:\ will be your 1st partion..here you can install two OS... 1st Windows Xp after that UBUNTU...after u done intalling two OS you can chose between the two OS.. 

Hope this will help

---

### Post by iSplicer on 2008-05-02
> **elord said:**
> i try this installing two OS in one PC..All you have to do is    1st install the Windows Xp and install the Ubuntu in same partition..No need for you to separate in installing Two OS in two partion..


C:\ will be your 1st partion..here you can install two OS... 1st Windows Xp after that UBUNTU...after u done intalling two OS you can chose between the two OS.. 

Hope this will help

wrong. You need the OS'es in different partitions - Ubuntu can't be installed onto a Windows-friendly file system!

YOU NEED TO MAKE A SEPARATE PARTITION!

---

### Post by zvacet on 2008-05-02
[Here]("http://psychocats.s465.sureserver.com/ubuntu/installing")

---

### Post by mlentink on 2008-05-02
> **elord said:**
> All you have to do is 1st install the Windows Xp and install the Ubuntu in same partition..No need for you to separate in installing Two OS in two partion..

Thanks for pointing to Wubi as an alternative install-method. There are advantages and disadvantages with that method. The OP seems to want to install using separate partitions. The link I gave will specify how to do that.

Wubi will not install in a separate partition, but in a virtual partition, which is actually a file in the windows-filesystem. Files can be erased a lot more easily than partitions.

Imho, Wubi is an excellent way to explore and discover Ubuntu with native speeds (rather than cd-speed), but if you plan on really making the switch, using separate partitions is the way to go...

---

### Post by iSplicer on 2008-05-02
Ohh.. He was talking about Wubi... lol, my bad and sorry!

---

### Post by sanjeevpunj on 2008-05-02
With my recent experience of a hard disk crash after installing UBUNTU, I suggest you definitely use a different partition for each OS, and better still a different Hard disk if you got a spare. My HDD crashed dueto many screwed up bad sectors and the device became unreadable totally.Itis definitely my Hard Disk that is to blame, perhaps UBUNTU was the last straw!

---

### Post by iSplicer on 2008-05-02
> **sanjeevpunj said:**
> With my recent experience of a hard disk crash after installing UBUNTU, I suggest you definitely use a different partition for each OS, and better still a different Hard disk if you got a spare. My HDD crashed dueto many screwed up bad sectors and the device became unreadable totally.Itis definitely my Hard Disk that is to blame, perhaps UBUNTU was the last straw!

Wrong. Dual booting works fine. His HDD just broke due to an unfortunate circumstance.

---

### Post by Sly-.- on 2008-05-02
Sweet, Just installed Ubuntu. Love it. :)

Edit:

Now is there a new up to date tutorial to get compiz up and running? Feel like messing about with it.

---

### Post by elord on 2008-05-05
i admit im wrong... install the windows at partition a and install ubuntu on partition b.. sorry bro..

---

