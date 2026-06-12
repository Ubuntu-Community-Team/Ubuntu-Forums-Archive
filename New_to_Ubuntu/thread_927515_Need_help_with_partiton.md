---
title: "Need help with partiton"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Max Bobo on 2008-09-23
Hi relatively new to Ubuntu 8.04

Installed dual boot on 2 HDD [ one for vista /one for Ubuntu ]
had a problem with Nvida graphic card directly after install ,and could not boot up anymore .anyway , installed Ubuntu again . now the Grub boot menu shows 
Ubuntu 8.04.1 ,kernel2.6.24-19-generic [ in the first line below all the usual , recovery mode and memtest 
than comes the 
other operating systems :
Vista .......
Ubuntu 8.04.1 ,kernel2.6.24-19-generic ( on/dev/sdb5)
Ubuntu 8.04.1 ,kernel2.6.24-19-generic (recovery Mode) ( on/dev/sdb5->)
Ubuntu 8.04.1, memtest86+ ( on/dev/sdb5)

they seem to be all partitons on the HDD, how can I merge them with the above one for Ubuntu ?

Thanks for the help

---

### Post by bumanie on 2008-09-23
That is normal to have all three listed
> Ubuntu 8.04.1 ,kernel2.6.24-19-genericboots the OS in 'normal' mode
> Ubuntu 8.04.1 ,kernel2.6.24-19-generic (recovery Mode)boots into recovery mode
> Ubuntu 8.04.1, memtest86+allows you to test ram modules for errors

---

### Post by Max Bobo on 2008-09-23
Thank You bumanie , I understand that part .
the problem is that under " other operating systems" it shows  Ubuntu another 3 times , with the addition of ( on / dev/sdb5 ) 

I checked the HDD through Vista disk management and it shows up with 6 partitions , as far as I'm aware a clean Ubuntu install only requires 3 , I have 6 , I want to reduce them to 3 and merge the lost space with the correct partitions .I also don't want Grub to show all the other Ubuntu versions as this will only confuse my wife when using the PC.
hope this makes sense ?

---

### Post by Bucky Ball on 2008-09-23
Normal. You can hide the other options but they shouldn't be on seperate partitions. Just wondering if you now have 3 Ubuntu partitions times 2 = 6 partitions. (Is this making Vista partition 7?) In Ubuntu, could you open a terminal (Applications->Accessories->Terminal) and copy and paste this:

**sudo fdisk -l**

Then copy and paste the results back into a post. :)

---

### Post by Max Bobo on 2008-09-23
here the output as requested , Thanks 


Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xece83e48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30720000    7  HPFS/NTFS
/dev/sda2            3825       47367   349748220    7  HPFS/NTFS
/dev/sda3           47367       48642    10241024    f  W95 Ext'd (LBA)
/dev/sda5           47367       48642    10240000    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2f7e25f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         606     4860352    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2             607       60801   483516337+   5  Extended
/dev/sdb5             607        1783     9454221   83  Linux
/dev/sdb6           59729       60801     8618841   82  Linux swap / Solaris
/dev/sdb7            1784       58654   456816276   83  Linux
/dev/sdb8           58655       59728     8626873+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Bucky Ball on 2008-09-23
```
/dev/sdb1               1         606     4860352    7  HPFS/NTFS
***Partition 1 does not end on cylinder boundary.***
/dev/sdb2             607       60801   483516337+   5  Extended
/dev/sdb5             607        1783     9454221   83  Linux
/dev/sdb6           59729       60801     8618841   82  Linux swap / Solaris
/dev/sdb7            1784       58654   456816276   83  Linux
/dev/sdb8           58655       59728     8626873+  82  Linux swap / Solaris
```I think the part in bold indicates there is a problem with your partition table, that could be why you can't boot into one of the two Ubuntus you have installed on that drive! You have your windoze setup fine on sda with 3 partitions (the 4th is the extended partition) and 5 partitions setup on sdb, 4 partitions are Ubuntu installed twice (2 partitions each - Ubuntu and it swap/s = 4).

```
/dev/sdb5             607        1783     9454221   83  Linux
 /dev/sdb6           59729       60801     8618841   82  Linux swap / Solaris
 /dev/sdb7            1784       58654   456816276   83  Linux
 /dev/sdb8           58655       59728     8626873+  82  Linux swap / Solaris
```Note you have two swap files on sdb. I suggest you need to delete sdb1 (as is NTFS and therefore belongs to windoze format), along with one of the Ubuntu installs then rewrite the grub. Also, sdb2 is an extended partition which Ubuntu/s is in, but not needed if you just have Ubuntu on this disk. I would personally be tempted to start again and reinstall Ubuntu on sdb. When it comes to the partitioning section, delete all the partitions on sdb and make 3:

 /
 /home 
/swap (about twice size of your RAM up to about a gig).

Might be easiest. :)

Bottom line - you have two Ubuntus in four partitions in an extended partition on sdb drive (2nd drive).

---

### Post by waspbr on 2008-09-23
i don't think you need more then one swap partitions, I have 3 Linux installations and windows on this computer and they (the linux installs obviously) use the same swap. 

Normally a ubuntu install only requires the root partition (/) and the swap, additional partitions are optional.

---

### Post by Bucky Ball on 2008-09-23
[quote=Max Bobo]Installed dual boot on 2 HDD [ one for vista /one for Ubuntu ]
had a problem with Nvida graphic card directly after install ,and could not boot up anymore .anyway , installed Ubuntu again .[/quote]

waspbr, Ubuntu is installed twice I would imagine.

---

