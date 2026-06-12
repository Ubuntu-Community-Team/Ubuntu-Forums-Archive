---
title: "using a boot disk to access a hard drive"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by justinohanoi on 2013-10-31
Hello happy Ubuntu world, 

My laptop (ubuntu 12.04) was updating, and something went badly wrong.  Now, whenever I start it, it doesn't recognize any of the external drives that are plugged in, can't detect the internet, doesn't allow me to access anything but my desktop screen, etc.  Basically it's nonfunctional.  Whatever went wrong, I'm happy to wipe the drive and update to 13.10.  Unfortunately, since the operating system won't recognize any peripherals, I have no way of pulling the data I need off the drive before I install 13.10.  I thought, no problem, I'll just run the boot CD and then use that to move the files I need.  Only problem, the operating system is password protected, so I don't have the right permissions to modify anything on the Old OS from the boot CD.  I know the password, I just don't know how to tell my hard drive, from the boot cd, that I know the password.  How can I access the files on the hard drive from the boot cd?  Any help would be greatly appreciated!  
 
Thanks
Justin

---

### Post by Redalien0304 on 2013-10-31
use Boot Repair Disk Available here [https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

---

### Post by fantab on 2013-10-31
Upgrades are often messy. Installing clean and fresh copy of latest version is one of the better options.

Boot with Ubuntu DVD/USB and opt to "Try Ubuntu without installing" (This does NOT need you HDD at all). Once the Ubuntu desktop is ready you can see all the HDDs and Partitions on the laucher. Click on the Partition you have you data on. Backup all the important data and do a clean install.

If possible create a simple ext4 formatted Partition without any mountpoint and use it to store your data. This way your data will be safe if anything goes awry with the install or upgrade or with the general functioning of the OS.

If you have any doubts or problem then post the output of:
```
sudo fdisk -l 
sudo parted -l
```

---

### Post by justinohanoi on 2013-10-31
Hi Fantab, 

I'm with you on the clean install.  My problem is that once I select "try ubuntu without installing" I don't have the permissions needed to back up the files on the HDD.  I'm assuming this is because the HDD is password protected.  The question is, how do I get permission?

Justin

---

### Post by fantab on 2013-10-31
By pasword protected you mean encrypted?
Try this:
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
 [http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)


If its not encrypted then perhaps you need to do this:
Click on the partitions you have your data on, then-
```
sudo nautilus
```

Navigate to /media/username/Partitions you are looking for.

---

### Post by Mark Phelps on 2013-10-31
If your hard drive is password-protected (as in encryption), then sorry, there is no way to work around that.

I've used several "work-provided" laptops over the years that had password-protected hard drives, and when something went wrong such that the password wouldn't work (as in, I forgot it!), there was no alternative other than to wipe the drive and re-image it.

---

