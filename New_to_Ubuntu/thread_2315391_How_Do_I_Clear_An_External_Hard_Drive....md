---
title: "How Do I Clear An External Hard Drive..."
date: 2016-02-28
forum: New to Ubuntu
---

### Post by wyattwhiteeagle on 2016-02-28
I have Ubuntu 14.04 LTS installed on a 8G USB Flash Drive.

How would I clear a 500G External HD that connects to USB port and check it for problems and correct them, etc.

Eventually, I wish to boot from the external USB 500G HD instead of the 8G USB flash drive.

The 500G has some problems that need to be corrected before I can pursue being able to boot from it.

---

### Post by HermanAB on 2016-02-28
gparted

---

### Post by Stephen_Soliday on 2016-02-28
These methods can be very destructive "UNDERSTAND WHAT THEY DO" before attempting them.

Only do this if gparted fails to do what you need.

First positively identify your drive. Without the external drive plugged in type:

   # cat /proc/partitions
   major minor  #blocks  name

      8        0  976762584 sda
      8        1     877568 sda1
      8        2   64000000 sda2
      8        3          1 sda3
      8        5  911882240 sda5

then plug in the external drive and do it again

   # cat /proc/partitions
   major minor  #blocks  name

      8        0  976762584 sda
      8        1     877568 sda1
      8        2   64000000 sda2
      8        3          1 sda3
      8        5  911882240 sda5
      8       16   31326208 sdb
      8       17    1078176 sdb1
      8       18       2272 sdb2

Notice the new device  "sdb"  that's the external

Try this first:

   #gdisk /dev/sdb

   Command (? for help): x

   Expert command (? for help): z
   About to wipe out GPT on /dev/sdg. Proceed? (Y/N): 
   (Y/N): y
   GPT data structures destroyed! You may now partition the disk using fdisk or
   other utilities.
   Blank out MBR? (Y/N): y

Now remove and replace the external USB drive an re-run gparted.

Alternatly wipe the whole drive (non-forensic)

   #dd if=/dev/zero of=/dev/sdb bs=4M

or just the MBR

   #dd if=/dev/zero of=/dev/sdb bs=512 count=1

---

### Post by sudodus on 2016-02-28
It depends on the problems.

1. If there are problems with the partition table or file system(s), ***gparted*** is a good tool.

2. If you think that there are hardware problems, bad sectors (physically bad spots on the disk surface) you can check the drive's S.M.A.R.T. information with ***smartctl***

```
sudo apt-get install smartmontools
man smartctl
```

If only a few bad sectors, is possible to mark them (in order to avoid them). For an **ext4** file system you can use ***e2fsck***

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number. If a large number of bad sectors, or if the number grows rapidly, the drive is failing, and you should rescue the information as soon as possible for example with ***ddrescue***. Stop using it except for cloning with ddrescue!!!

```
sudo apt-get install gddrescue
info ddrescue
```

3. There might also be mechanical or electronical problems, that make the HDD unreliable. You should rescue the information as soon as possible for example with ***ddrescue***. Stop using it except for cloning with ddrescue!!!

-o-

***Edit: ***See also these links:

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by X-RED_Tech on 2016-02-28
+1 to the post above.

I would like to add that if you have the situation described in point 3 then you should not try to install in there.

---

