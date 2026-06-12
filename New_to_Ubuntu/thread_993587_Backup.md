---
title: "Backup"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by bigal1932flying on 2008-11-25
I am having so much trouble with 8.10 that I will have to make some change either back to Hardy or a reload of Ibex. But I first want to back up my emails, photos etc.
Is there an easy way to do this? I have tried installing pybackpack but this does not work.

---

### Post by aheckler on 2008-11-25
If you have a large enough external drive, just plug it in and then drag and drop your stuff onto it. Presto!

---

### Post by sstusick on 2008-11-25
If you have a separate /home partition, there is no need to back anything up. All you have to do is format the / partition then re-install Ubuntu and set your /home partition as the /home partition for the new install.

---

### Post by doyouhas on 2008-11-25
If you want to be extra sure, and you don´t have any external media, upload essential files to a service like _[File Den](http://www.fileden.com)_ and then download them once the upgrade is complete.

---

### Post by mapes12 on 2008-11-26
Basically, all the stuff you want to keep will be in your /home directory. Back this up and you will be good to go for a clean install.

If you haven't got /home on a separate partition then this HowTo may help: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)  That way all you need to do is reinstall Ubu onto your /(root) partition making sure you select the "Manual" option when you get to the partitioning stage. Then select each partition and set the variable so that the installer knows where you want it to install /, /home and swap.

This way you would not need to backup anything but personally I would just to be on the safe side of things.

---

