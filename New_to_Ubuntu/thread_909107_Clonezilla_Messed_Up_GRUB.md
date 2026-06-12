---
title: "Clonezilla Messed Up GRUB"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by bjstabio on 2008-09-03
I used Clonezilla to copy the entire disk sda onto sdb.  When Clonezilla asked if I wanted to install GRUB into the MBR of sdb, I said yes.  I have four OS installed on sda and they were all available prior to the use of Clonezilla.  Now the only OS that appears on the GRUB menu at boot-up is located on sda2 (hd0,1).  The OS on sda9 (hd0,8) was the last one installed and was the default.  I have to admit that I seem to have a mental block when it comes to GRUB.   I tried to find some help online and found and used the following:

grub> find /boot/grub/stage1 
 (hd0,1) 
 (hd0,4) 
 (hd0,6) 
 (hd0,8) 
 (hd1,1) 
 (hd1,4) 
 (hd1,6) 
 (hd1,8) 

grub> 

Does this mean that I can select any one of these as the grub root, i.e. grub> root (hd0,8)?  Any help would be very much appreciated.

---

### Post by bumanie on 2008-09-03
Post the output of > sudo fdisk -lAlso, do you have any idea where grub was installed to before? Were the other OSes being chainloaded? What are the other OSes? Did you happen to have a backup of your /boot/grub/menu.lst prior to using clonezilla? Suggest you read Herman's [grub page]("http://users.bigpond.net.au/hermanzone/p15.htm") It explains how to setup multiple boot systems with grub and many other things about grub.

---

### Post by caljohnsmith on 2008-09-03
Do you by chance still have everything on sda as it was, or have you all ready deleted/modified that HDD? If you haven't modified sda, then boot into any Linux OS, run the following command, and post the output:
```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
```
The output is in hex and may look useless, but it will tell us which Linux OS on that HDD is in control of Grub in the MBR. Once you know that, then we can help you set up sdb so it is exactly the same.

---

### Post by bjstabio on 2008-09-04
bjstabio@BobbyBuilt:~$ sudo fdisk -l 
[sudo] password for bjstabio: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00053aa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         130     1044224+  82  Linux swap / Solaris
/dev/sda2   *         131        6604    52002405   83  Linux
/dev/sda3            6605       19457   103241722+   5  Extended
/dev/sda5            6605       10577    31913091   83  Linux
/dev/sda6           18930       19457     4241128+  82  Linux swap / Solaris
/dev/sda7           10578       14514    31623921   83  Linux
/dev/sda8           18584       18929     2779213+  82  Linux swap / Solaris
/dev/sda9           14515       18410    31294588+  83  Linux
/dev/sda10          18411       18583     1389591   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00053aa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         130     1044224+  82  Linux swap / Solaris
/dev/sdb2   *         131        6604    52002405   83  Linux
/dev/sdb3            6605       19457   103241722+   5  Extended
/dev/sdb5            6605       10577    31913091   83  Linux
/dev/sdb6           18930       19457     4241128+  82  Linux swap / Solaris
/dev/sdb7           10578       14514    31623921   83  Linux
/dev/sdb8           18584       18929     2779213+  82  Linux swap / Solaris
/dev/sdb9           14515       18410    31294588+  83  Linux
/dev/sdb10          18411       18583     1389591   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

I believe GRUB was installed on sda8.  No chainloading.  All of the OS are Ubuntu derivatives or Debian.  No backup of menu.lst

---

### Post by bjstabio on 2008-09-04
bjstabio@BobbyBuilt:~$ sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
2 bytes (2 B) copied, 2.8361e-05 s, 70.5 kB/s
0000000 0000                                   
0000002

Hope this helps.  Thanks!

---

### Post by bumanie on 2008-09-04
I am not experienced with so many OSes. To setup grub on /dev/sda8 the terminal code would be > sudo grub > root (hd0,7) > setup (hd0)>  quitThen reboot and see what happens. As I said,never tried dealing with so many OSes, but if you are correct that grub was on /dev/sda8, the above code should work.

---

### Post by caljohnsmith on 2008-09-04
I think I misunderstood your original post. Are you saying the sda Grub menu on start up is the one with the problem? And when you say:
[QUOTE=bjstabio]The OS on sda9 (hd0,8) was the last one installed and was the default.[/QUOTE] 
Are you saying that when you installed sda9, you let it install Grub to the MBR, so sda9 was controlling the MBR? If that is true, you can give sda9 control of the MBR again by doing the following:
```
sudo grub
grub> root (hd0,8)
grub> setup (hd0)
grub> quit 
```
If you do what Bumanie mentioned, then sda8 will have control of the MBR instead of sda9. I don't think that is what you want, but like I said, I may be misunderstanding. Please clarify or let us know what you decide to do.

---

