---
title: "Simple question re installation"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by doctored on 2008-05-22
I am playing around with Hardy on a Compaq Presario. If I can get the Broadcom wireless card to work I plan to start using it much more.
At the moment I am running Hardy Heron off the CD. If I choose the 'Install' option, how does a Windows laptop handle this? I do NOT want my Windows installation over-written. Presumably the hard drive has to be partitioned - does the Ubuntu installation CD handle this automatically?
Thanks.


Middle-aged would-be Ubuntu nooby
Yorkshire
UK

---

### Post by doctored on 2008-05-22
I've answered my own question [here]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html").

---

### Post by Phoenixzeus on 2008-05-22
You can use WUBI if you like, and therefore you wouldn't have to play around with partitions, but I would recommend using a program like Partition Magic to resize your NTFS (presumably) partition down to make way for the Linux Ext3 / swap partitions.

---

### Post by doctored on 2008-05-22
Oh Lord now I'm confused.
The link above has this paragraph:

Partitioning does not occur until you finalize the installation, so you can decide to abort the installation at the very last minute if you require. After finalizing the installation, however, the hard disk will be re-partitioned and all existing data stored on it will be lost. Ensure that you have made and tested a backup copy of all important data.

Does this mean I need to re-install Windows after installing Ubuntu? This will be a problem as the Compaq I'm planning to use did not come with a Windows restore disc.

---

### Post by shifty_powers on 2008-05-22
ok, what exaclty are you planning to do?

are you going to let ubuntu resize your windows partition and create a linux partition?

if so, then yes, always back up your data, but it is plaing wrong that it will destroy all the data on your windows partiton.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

will give you better advice i think.

---

### Post by starcannon on 2008-05-22
Some things to try might be:

[http://wubi-installer.org/](http://wubi-installer.org/)

If you want to resize your windows partition to allow full ubuntu install:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Take your time, read thrice, install once, BACKUP ALL important data before you do this (you can probably buy a restore disk from your oem for $20 double check for availability I know our HP has that option)

Good Luck
~Starcannon

---

### Post by didac on 2008-05-22
Partitioning and resizing are different -- though resizing is a repartitioning without destroying data. Resizing is safe, unless you have a power blackout . . . You have to know your free space before hand and don't make a partition smaller than the data you already have. The resizing program will check your hard disk for errors, and if there is the slightest inconsistency in your data it will refuse to resize, until you check your hard disk under windows.

If you are not very conversant with partitioning, let the installer resize your windows partition, not partition it. Make sure it gives you enough free space for Windows to continue running. Say you have 100 G free in Windows, and you resize Windows by 95 G, that will give you only 5 G for Windows, 95 G for Linux. Not a good idea.

Repartitioning is different: it destroys your data and you start all over again.

Once you resize and install linux, you'll be able to boot to Windows too.

---

### Post by lswest on 2008-05-22
for your broadcom card, you may want to have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=780212") specifically my post (#5) has a link to a driver for some broadcom cards and the way i got my card running, which may help you out.

About partitioning, if you manually partition the system and resize your windows partition to make room for Ubuntu, then no, the files will not be removed, but be sure to defragment Windows first (Vista does this in the background while it's running, so it is less necessary).  Just be careful with what you do when you're partitioning.

---

### Post by philinux on 2008-05-22
I'd back up anything important and create a restore disk too. And make sure it will boot.

---

