---
title: "Transfering software sources list"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by kingdraco41 on 2012-07-09
I was hoping to change from my wubi-installed Ubuntu version to a proper partition, but I cannot fully remember every single piece of software I've installed. Instead of having to go to the software sources center (SSC), write down the list of software sources I've installed (possibly missing a few, since the SSC GUI omits some of the packages), I was wondering if there is a way to transfer the list to the new OS.

When upgrading from 11.10 to 12.04, Ubuntu did this itself; finding the packages it needed for the programs and installing them. However, I cannot tell whether this was a just a result of the SSC list being stored in the user account - and the installer used that information to download them, or if there is something additional I need to do.

Thank you.

---

### Post by NikTh on 2012-07-09
> **kingdraco41 said:**
> I was hoping to change from my wubi-installed Ubuntu version to a proper partition, but I cannot fully remember every single piece of software I've installed. Instead of having to go to the software sources center (SSC), write down the list of software sources I've installed (possibly missing a few, since the SSC GUI omits some of the packages), I was wondering if there is a way to transfer the list to the new OS.

If you still have this wubi-installation consider to switch to normal install with this way --> [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) , i never did that but you can try it if you want. 

For software sources , all your lists of PPA's are in /etc/apt/sources.list.d/ , write them down . See the list from terminal with this command ```
ls /etc/apt/sources.list.d/
```All your installed software is a big list in dpkg's memory. First clean up the cache with ```
sudo apt-get autoclean
``` and then open a terminal and give this command 
```
dpkg -l | awk '/^ii/ {print $2, $3}' > pkgslist.txt
``` a pkglist.txt will be created in your home folder . Open it with ```
gedit pkglist.txt
``` and you will see all the packages which you have installed. (I think not only those , but ALL the packages which are installed in Ubuntu)

---

### Post by Double.J on 2012-07-09
Hi there!

Would you be interested in this [Howto]("https://help.ubuntu.com/community/MigrateWubi") on moving wubi to a full install?

As for starting from scratch and adding the packages, copying them is one way; check out [Cynical's guide]("http://ubuntuforums.org/showthread.php?t=261366"). The start of the command he recommends, ```
 dpgk --get -selections
``` alone will list every package you have installed.

The problem with doing a full package list is it doesn't differentiate between the packages ubuntu came with, packages you've added, or, if you don't use features such as auto clean and purge, dependencies of packages you don't even have any more.

If you did want to start from scratch, it may just be worth making a note of the actual programs you use and adding those in post install to keep it fresh - many new users add far more packages to try out than they will ever use.

Don't forget if starting from scratch, you can install Ubuntu to your hard drive, whilst still having wubi on the computer.

Hope it helps!

---

### Post by kingdraco41 on 2012-07-10
Okidoke. Thanks ya'll. I didn't even know there was a way to migrate wubi to a partition. I'll be sure to give that a thrice-over. I am curious, however, on how the tutorial expects one to partition the drive. In my experience, that can only be done externally with some OS off a live CD or USB. Does Ubuntu support partitioning a mounted drive and I just haven't heard of it?

Edit:
I mean, I know how to partition a drive using a live boot CD (I used wubi because I wanted to test Ubuntu's ability on my new computer), I am just curious. As well, I am away from any burnable CDs for the time being, so if there is a way, it could give me the ability to install Ubuntu sooner.

---

### Post by O2Blevel on 2012-07-10
Sorry, wrong thread

---

