---
title: "how i do this!!!!"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by nnamdi on 2008-07-03
hello all i want to upgrade from gusty to hardy and i got two partition on gusty

/root and
/home

i have a lot of stuffs on my home part i dont want to loose any doc at all how do i go about it

---

### Post by piousp on 2008-07-03
you can just type:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

and your done ;)

---

### Post by phidia on 2008-07-03
Make sure you backup your home. Everything should work fine but always back up anyway.
Open up the update manager and select distribution upgrade.

---

### Post by nnamdi on 2008-07-03
how long will it take cos my connection is 10kb/s and are mine suppose to issue in the three commands at the same time

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by benfindlay on 2008-07-03
put the commands in one after the other. 10kbps will take a long time to download everything too

---

### Post by philinux on 2008-07-03
> **nnamdi said:**
> hello all i want to upgrade from gusty to hardy and i got two partition on gusty

/root and
/home

i have a lot of stuffs on my home part i dont want to loose any doc at all how do i go about it

Send of to canonical and get a live cd. 10kb/sec will take ages to upgrade. you can then do a fresh install but leave /home as not to format during the installation phase. Just format /.

---

### Post by nnamdi on 2008-07-03
but i hv the hardy cd so wat do u think? cos we are not allow to bring our private computers to the office so can i do it wit the normal cd

---

### Post by piousp on 2008-07-03
You can do it with the live cd too. Just dont format your /home partition, and your all set.

---

### Post by aashay on 2008-07-03
Actually, get the alternate Cd and follow these instructions. That is what I did
> Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download and burn the alternate installation CD.
   2. Insert it into your CD-ROM drive.
   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions. 

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

kdesu "sh /cdrom/cdromupgrade"
Instructions lifted from [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

### Post by nnamdi on 2008-07-04
please i would like to ask is the installation cd the same as the alternate cd too cos when i booted with the live cd i saw some like alternate below

---

### Post by sayakb on 2008-07-04
The Alternate CD is just like the LiveCD without a GUI. In simpler words, you need to use the keyboard in the alternate install CD rather than the keyboard+mouse in the LiveCD (but this is when you go for a clean install). The installation process is clear and self explanatory. Though you must have basic knowledge about partitioning.

---

### Post by nnamdi on 2008-07-04
ok then seems i have download the alternate too cos i have to upgrade from gusty to hardy, i had cd/dvd rom but has been fixed. but are they commands that i have to follow?

and also i have three partitions

/ 37gb
/home 72gb
/Data 37gb

i want give more space to home from root partition without loosin data. during the process of reformattin my root part. how do i go about it

---

