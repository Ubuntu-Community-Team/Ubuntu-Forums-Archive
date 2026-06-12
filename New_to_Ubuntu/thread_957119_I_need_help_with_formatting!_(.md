---
title: "I need help with formatting! :("
date: 2008-10-23
forum: New to Ubuntu
---

### Post by SilverShadow118 on 2008-10-23
I'm a new user to Ubuntu - so far, it has exceeded all of my expectations minus one area: its inability to recognize and format NTFS drives. I'm using it live right now and going in through Windows, sadly, isn't an option. Please help :(

---

### Post by eternalnewbee on 2008-10-24
Hi there.
That's strange. I don't dual boot with xp anymore, but when I did there were no problems. 
Have you mounted Windows? If you don't understand this, go to Computer and right click on the windows icon and left click on Mount Volume.
Good luck.

---

### Post by SilverShadow118 on 2008-10-24
Heh ^_^; I'm a bit confused as to what exactly you mean. Could you please go into detail? >.<

---

### Post by eternalnewbee on 2008-10-24
Wait. I'll send you a screenshot

---

### Post by eternalnewbee on 2008-10-24
In the second screen shot you see four icons.
File system is where Ubuntu is installed. On your computer you should see an icon of the windows drive. Right click it and choose mount.

---

### Post by eternalnewbee on 2008-10-24
Like this:

---

### Post by Piraja on 2008-10-24
> **SilverShadow118 said:**
> inability to recognize and format NTFS drives
Until someone more knowledgeable* comes along to help you, I would just say that Ubuntu should indeed be able to recognize and format NTFS drives, as far as I know. 

I have Ubuntu installed on a 500 GB external USB hard disk drive, while the same drive has also one NTFS partition and the internal drive has WinXP on NTFS, too. The NTFS partition on the external drive is mounted automatically in Ubuntu, and so is presently also the internal hard drive. Windows does not recognize Linux partitions, but Linux does recognize Windows file systems.

Could you be a little more specific &#8212; were you stuck at the LiveCD's installer's partitioning phase, or did you try GParted (System > Administration > Partition editor)? Is the NTFS drive mounted (does an icon appear on your desktop)? If it is, you must unmount it before partitioning or formatting.

In any case, Ubuntu cannot be installed on an NTFS partition, I think. But I suppose that's not what you're trying to establish?

* EDIT: Eternalnewbee replied while I was writing the above. Pretty fast! I wish you the best of luck!

---

### Post by eternalnewbee on 2008-10-24
Any progress?

---

### Post by SilverShadow118 on 2008-10-24
No progress at all >.< I think we're using different versions of Ubuntu. Gparted displays no hard drives. I'm sorry, but I'm very confused >.<

---

### Post by eternalnewbee on 2008-10-24
So, what version are you using?

---

### Post by SilverShadow118 on 2008-10-24
I believe it's called Hardy Heron, or something like that.

---

### Post by eternalnewbee on 2008-10-24
Could you go to Computer and make a screen shot?

---

### Post by eternalnewbee on 2008-10-24
Me too...

---

### Post by SilverShadow118 on 2008-10-24
[[IMG]http://img266.imageshack.us/img266/1576/screenshothh4.th.png[/IMG]](http://img266.imageshack.us/my.php?image=screenshothh4.png)[[IMG]http://img266.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by eternalnewbee on 2008-10-24
I see. Ubuntu doesn't see another Drive.
Question: When you boot up the system, do you get the option to boot Windows?

EDIT: I think I know why: It's because you are running the Live CD.
But if Ubuntu is installed on your computer, then mounting and formatting should not be a problem.

---

### Post by SilverShadow118 on 2008-10-24
I do get the option to boot up windows (during my time gone I was reinstalling windows). I have xp pro that I placed on one of two partitions on the drive only so I could try to install Ubuntu through windows (excuse my run-on sentence ^^). Is there a way that I could format a partition of the drive to something like FAT32 or ext3 as a Live Session User or through Windows?

---

### Post by SilverShadow118 on 2008-10-24
Though, when I boot from the CD and choose 'Install Ubuntu', everything works fine until step number 4 -- where I must choose which drive to install Ubuntu. The field is blank.

---

### Post by eternalnewbee on 2008-10-24
As you got the blank field, there might be a problem with the cd. Try and download the Hardy Heron LTS version and burn it at speed 4. Then boot from the cd.
Good luck.

---

### Post by eternalnewbee on 2008-10-24
Btw, during installation you'll get the option to format the partition. Choose Ext.3

---

### Post by SilverShadow118 on 2008-10-24
I'll try that. Thank you.

---

### Post by eternalnewbee on 2008-10-24
You're welcome.

---

### Post by bhaverkamp on 2008-10-24
A default 7.04 or later ubuntu should have installed the ntfs-3g driver which would allow the use of ntfs file systems. This is usually the default when setting up a dual boot system which was already running windows. Use package manager to check for this package. If it's already marked installed try using gparted to browse your drives. gparted will let you mount partitions by right clicking on them. If this works then all you need to do is setup your /etc/fstab file to mount the partition on boot.

---

