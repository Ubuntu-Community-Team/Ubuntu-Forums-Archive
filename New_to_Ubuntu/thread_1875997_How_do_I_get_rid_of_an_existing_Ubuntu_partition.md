---
title: "How do I get rid of an existing Ubuntu partition ?"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by vincej on 2011-11-05
Hi - when i installed 11.10 I accidentally it on a disk which had an existing 11.4 Ubuntu partition. I want to get rid of the 11.4 partition. 

How do I do this - in kindergarten terms please :o)

Many Many thanks!

---

### Post by dave0109 on 2011-11-05
You could use the program 'gparted', which may or may not be installed on your computer.  If not, start the Ubuntu Software Centre and search for gparted.  Once installed you can run it up and it will show you all partitions on your disc.

Make sure you understand which partition it is that you want to delete.  The program should stop you deleting the one that you are using, but make sure you don't delete any windows partition for example.  It's most likely that the partition you want to remove is 5 or higher.  But check, then double check.  And make a backup.  Then check again. :D

---

### Post by drs305 on 2011-11-05
Boot into 11.10. Then make sure the 11.10 bootloader is controlling things by running the following command; X is your boot drive (a,b,c, etc)

```
sudo grub-install /dev/sdX
```
Example: sudo grub-install /dev/sda

Reboot and make sure the 11.10 menu item is at the top of the Grub 2 menu when you boot. After booting, you can remove the 11.04 partition using Gparted.
```

gksu gparted
```
The 11.04 partition should not be mounted (no 'key' icon next to it in the bottom panel of Gparted).
Click on the 11.04 partition to select it. 
Partition > Delete.

Run "sudo update-grub" to update your Grub 2 menu:
```
sudo update-grub
```

If you have an entry in fstab for that partition, you should remove it.
```
gksu gedit /etc/fstab
```

Another option would be to just reformat the partition to erase the current files and then use it as a data partition. In that case, Partition > Format to > and then choose the format.

---

