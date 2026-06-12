---
title: "Difference between install sizes"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by 8gigs on 2008-08-06
Hello everyone. I am new to Ubuntu and Linux in general. The first obstacle I ran into when trying to setup Ubuntu (and possibly, this applies to other Linux distros) is that it asks for an install size. I cannot find any information about how this will affect the operating system. It says 4gb is minimum and 8gb is recommended, which leaves me a little daunted because my Windows install uses less than 3gb. Exactly what is the space needed for and what will happen if I specify a lower amount?

---

### Post by bobnutfield on 2008-08-06
You are correct that different distros require different install space.  A full install of Ubuntu with the Gnome desktop will use about 3GB  I believe.  If you specify less than the recommended amount, you may run into storage problems.  Many, including myself, use a different partition for /home (data), which solves a lot of space issues.  The 8GB recommendation is usually if you do not specify a different partition for home.

---

### Post by halitech on 2008-08-06
first, how are you trying to do the install?

second, most times you will want the space after you get going. I have a 160gig drive and at any given time I could have my home folder (about 80gig) be anywhere from 20% to 85% full so its not hard to use the room.

---

### Post by jimv on 2008-08-06
I just did a fresh install of Ubuntu 8.04 and it takes up about 2.1 GB of space.

It will install on less than 4 gb...though if you go too much lower than that, it will say that partition is not large enough.  I'm not entirely sure how much less though.  I installed it on a 4 GB thumbdrive, and I think it used about 600 mb for SWAP space.  So perhaps you could get away with a 3.5 gig partition, but then you still need a SWAP partition.  You could always shrink the partition down to about 2.5 gigs after the install by using a partition editor like Gparted, but that won't leave much room for doing much of anything.

And what version of Windows are you using that takes only 3 gigs?

---

### Post by halitech on 2008-08-06
just checked my laptop and I have 3.4 gig used (have ubuntu-desktop and xubuntu-desktop installed and most basic needed files)

My desktop on the other hand, has ALOT of stuff installed I use daily
```

daryl@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              56G   11G   42G  20% /
varrun                443M  480K  442M   1% /var/run
varlock               443M     0  443M   0% /var/lock
procbususb            443M   96K  443M   1% /proc/bus/usb
udev                  443M   96K  443M   1% /dev
devshm                443M     0  443M   0% /dev/shm
lrm                   443M   34M  409M   8% /lib/modules/2.6.22-15-generic/volatile
/dev/sda1             228M   42M  175M  20% /boot
/dev/sda4              89G   41G   44G  49% /home
/dev/sdb1             190G   77G  114G  41% /media/New Volume
daryl@ubuntu:~$

```

---

### Post by snowpine on 2008-08-06
Storage is cheap these days, I'm sure you can find 4gb to spare! :-)
If you are really, truly concerned about it, you can do a minimal install ([http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)) and then build up whatever you need from there. But since you are new to Ubuntu, I would not recommend it.

I have linux on an old laptop with a 6gb hard drive, with 3 separate partitions (/, /home, /swap) so I know it can be done.

---

### Post by ntu on 2008-08-06
I have feisty on a 3.8gb partition and 2.9gb is used. I also have a swap partition.

---

### Post by 8gigs on 2008-08-07
> **halitech said:**
> first, how are you trying to do the install?

I was doing a dry-run of the installer from within Windows. If I actually install Ubuntu I will make a new partition and install from the live boot.

> **jimv said:**
> And what version of Windows are you using that takes only 3 gigs?

Win2k, and that figure includes 8 years' worth of Windows Updates/Service Packs (about 500mb). If you disable the extra features in XP, namely Hibernation and System Restore, it uses about the same amount of space. Granted though, Vista wants 15gb.

@various: I'm glad to hear that it's possible to install Ubuntu using less space. But I'm still wondering what the difference is between a 4gb install and an 8gb install. Is there a difference or is the installer just blowing hot air?

---

### Post by mcduck on 2008-08-07
The main reason why Ubuntu takes more disk space than Windows is quite obvious, when you think about it: Ubuntu comes with a load of programs, while Windows itself doesn't really include much more than the OS itself and couple of basic tools.. Add  a good image editor, full office suite, music players, video players, codecs and everything else and you'll soon end with a noticeably larger disk usage.. ;)

If you make a CLI install of Ubuntu, and then only add the programs and features you need you'll easily squeez Ubuntu to something like 1-2GB.

Other Linux distributions have even smaler disk footprint, Damn Small Linux only needs 50MB, SliTaz disk image is less than 30MB (installed syste takes 80MB) and depending on what you need even smaller installs are possible ;)

---

### Post by snowpine on 2008-08-07
> **8gigs said:**
> But I'm still wondering what the difference is between a 4gb install and an 8gb install. Is there a difference or is the installer just blowing hot air?

The difference is 4gb of empty space for your personal files. :)

---

