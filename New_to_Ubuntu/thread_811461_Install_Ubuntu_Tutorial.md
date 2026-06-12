---
title: "Install Ubuntu Tutorial"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by bern1939 on 2008-05-29
There are lots of tutorials to show one how to partition a disk between Windows & Ubuntu.
I have a hard drive with 78GB space and wish to install 8.04 on it with nothing else.

I want to do that_ manually_ rather than via the automatic route....might learn something too!!

Is there a good tutorial available to show one......step by step???

Thanks


Bern

---

### Post by Aearenda on 2008-05-29
[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml) may help. Or [http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron).

I usually create a 10Gb ext3 partition for /, a 1Gb swap partition (I have 1Gb RAM), and then use the rest for /home also as ext3. If it is a bigger drive and I want the system to last a long time, I add a second 10Gb partition to be made a copy of / so I can revert upgrades that fail.

---

### Post by hyper_ch on 2008-05-29
Well, there is not much difference, just select manual partitions and know what you need/want...

recommended are at least 3 partitions:

Partitions:
/ --> root
/home --> where user data is stored (although I don't use that anymore)
swap

Filesystems
/ and /home are recommended to be formatted to ext3
swap requires to be designated as swap

Sizes
with your 78 GB I recommend
/ --> somthing between 6-10 GB
swap --> twice your ram (up to max. 1 GB [if you don't use VMs or resources intense applications you can even make it smaller])
/home --> all the rest

Specials:
/ --> this must be flagged as bootable

In the installer you select empty space and select to create new partition, then you can enter the size of it and also select whether it shall be a primary one.

To set the file system or boot flag, enter the partitions created. You get then a menu which is quite simple. Select ext3 or swap from the drop down and hit enter upon the boot flag option.

----------------

If you want to go and install an encrypted system (alternate or server cd) then you will require an addition /boot partition. Make it about 100mb (more if you want to keep different kernels) and use Ext3 as filesystem. In that case make thise partition bootable and no the / one.

---

### Post by Abu_Dayya on 2008-05-29
[http://screencasts.ubuntu.com](http://screencasts.ubuntu.com)

It has video tutorials on lots of things, including installing ubuntu. Its about gutsy though, not hardy. But the installation is identical

---

