---
title: "Installing Kubuntu KDE 4 Remix on Ubuntu Gutsy + XP dual boot system"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by aachen on 2008-04-25
Hello all,
I have a dual boot system with Ubuntu gutsy and windows XP. Now I want to d0 a fresh install of new KDE 4 remix in place of gutsy and want to keep the XP partitions same as before without any change. Is this possible? I dont want to loose any data from windows or format the windows drives. I already have the live CD of KDE 4 remix.
Thanks in advance.

---

### Post by meborc on 2008-04-25
> **aachen said:**
> Hello all,
I have a dual boot system with Ubuntu gutsy and windows XP. Now I want to d0 a fresh install of new KDE 4 remix in place of gutsy and want to keep the XP partitions same as before without any change. Is this possible? I dont want to loose any data from windows or format the windows drives. I already have the live CD of KDE 4 remix.
Thanks in advance.

you should be able to install kde on your ubuntu partition... then the win partition will be left untouched... just be sure which partition you assign for the kde while installing

---

### Post by aachen on 2008-04-25
I am not sure whether it will install KDE on only gutsy partition. It did not inform me such thing when I tried to install so I quit installation as I was not sure. I could not find any help over the internet about this topic. Has anybody done such a thing ?

---

### Post by Paqman on 2008-04-25
> **aachen said:**
> Is this possible?

Absolutely. When  you run the installer choose "manual partitioning". Select the partition that currently has Gutsy on it. Check the box for it to be formatted and set the mount point as /.

That will install a fresh copy of Hardy over the top of Gutsy.

---

### Post by aachen on 2008-04-25
It only shows me /dev/sda partition when I select manual mode. and says your partition #1 and #5 will be formatted. now I dont know what is this partition #1 and #5 and in which partition is my ubuntu and which partition is windows. I just know that my C drive is windows and partitions E, F and G are also NTFS. D drive is DVD drive. I was afraid that it would format windows so I quit the setup. can someone explain in simple termiinology ? and what is this mount point ?

---

