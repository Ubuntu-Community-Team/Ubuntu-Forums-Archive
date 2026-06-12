---
title: "[SOLVED] Re-Partitioning after installation?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Ingenue on 2008-07-28
Hi, I was wondering if anyone would be able to help. I am dual booting Vista and Hardy, during the installation process I devoted more space to vista since I was brand new to Linux and Ubuntu. Now I would like to go back a devote more space to Ubuntu. However I would like to not have to re-install Ubuntu if possible, as it was such a pain to configure my wireless card. Lazy I know.

I have searched Google and these forums and can not seem to find what I am looking for. Any suggestions?? :confused:

---

### Post by DGortze380 on 2008-07-28
> **Ingenue said:**
> Hi, I was wondering if anyone would be able to help. I am dual booting Vista and Hardy, during the installation process I devoted more space to vista since I was brand new to Linux and Ubuntu. Now I would like to go back a devote more space to Ubuntu. However I would like to not have to re-install Ubuntu if possible, as it was such a pain to configure my wireless card. Lazy I know.

I have searched Google and these forums and can not seem to find what I am looking for. Any suggestions?? :confused:

post the output of 
```

df -l

```

But more than likely you'll want to do this.
Use your live cd, open a terminal and type 

```

sudo gparted

```

This program will allow you to shrink your ntfs partition, move ext3 over and grow ext3.

Back up all data before you do this as moving partitions can cause them to become corrupt.

---

### Post by halitech on 2008-07-28
if you have vista, use the built in tools to defrag the windows partition a few times, then you should be able to resize the windows partition. then boot the Gparted cd and resize the Ubuntu partition

---

### Post by kansasnoob on 2008-07-28
I'd personally use Vistas own partitioning tools to resize the Vista partition and then use Gparted to resize the Ubuntu partition(s).

If you use Gparted to resize a Vista OS partition you're very likely to need this:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

And, if you have no Vista recovery disc, you'll likely need this:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by kansasnoob on 2008-07-28
I like this link better if you do find that you need to restore Vistas MBR:

[http://www.winvistatips.com/fix-mbr-a116.php](http://www.winvistatips.com/fix-mbr-a116.php)

It's just better!

---

### Post by Ingenue on 2008-07-28
```
melissa@melissa-laptop:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             31454368   2797760  27071396  10% /
varrun                 1033068       120   1032948   1% /var/run
varlock                1033068         0   1033068   0% /var/lock
udev                   1033068        52   1033016   1% /dev
devshm                 1033068        64   1033004   1% /dev/shm
lrm                    1033068     39776    993292   4% /lib/modules/2.6.24-20-generic/volatile
gvfs-fuse-daemon      31454368   2797760  27071396  10% /home/melissa/.gvfs
/dev/scd0               711154    711154         0 100% /media/cdrom0
/dev/sda1             39222660  17962300  21260360  46% /media/disk
/dev/sda2              5807496   4704488   1103008  82% /media/PRESARIO_RP
```

That was the output of the df -l command.

So very lost. I put in my live cd(the intallation disk right?) and tried the sudo gparted command and it said the command was not found.

---

### Post by halitech on 2008-07-28
```
sudo apt-get install gparted
```

that will install it and then you should be able to run gparted

---

### Post by kansasnoob on 2008-07-28
Did you read what I posted previously?

I'll find you a Vista partitioning tutorial if you'd like.

But to use Gparted to do your resizing you need to boot the Ubuntu Live CD and select "Try Ubuntu without any change to your computer". Then once you're running in the Live CD go to Administration > Partition Editor.

You'll need to make your changes using Partition Editor (aka, Gparted) from the Live CD because partitions must be unmounted to do anything with them. Once looking if you're confused just shout. Better safe than sorry!

There are many great tutorials about partitioning using Gparted.

---

### Post by Ingenue on 2008-07-28
Yes thank you I have read each post carefully. Very frustrated. My Live disk is not booting properly and gparted is not allowing me to unmount the drives. It says I need to manually unmount them. The live disk gives me a black error screen saying Logical error.

You know what I would really like to do is just wipe vista off completely, I just don't want to lose all of the Ubuntu setting I now have. 

I can not tell you how much your help means to me. Thanks, Melissa

---

### Post by bodhi.zazen on 2008-07-28
You *should* manage your partitions from a live CD (you can not resize a mounted partition, thus you can not resize your Ubuntu partiton while renning Ubuntu from hard drive).

You can use the Ubuntu CD or you can download a live Cd :

[Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

[http://partedmagic.com/downloads/stable/](http://partedmagic.com/downloads/stable/)

The iso image is distributed in a zip file.

---

### Post by nayanm on 2008-07-28
From an administrator account in Windows Vista, go to Start > Control Panel > System and Maintenance > Create and format hard disk partitions .

Then right-click on your Vista partition (mine says C:\ "Boot, Page File, Crash Dump, Primary Partition") and select Shrink Volume. Enter how many megabytes you want to shrink the Vista partition by and then press the Shrink button. Vista will then shrink this partition.

After this, insert your Ubuntu Live CD and run Gparted. (sudo gparted) Right-click on your Ubuntu partition and select Resize/Move. You can then enlarge the partition to fill up the remaining space.

That is, if you haven't deleted Vista by now ;)

(But seriously, if you want to delete Vista, open Gparted and right-click on you Vista partition. Then select "Delete." After that, enlarge your Ubuntu partition to fill the remaining space.)

Good luck!

---

### Post by Ingenue on 2008-07-28
Ok, So I made a live Cd of gpart and resized my vista partition. Vista is intact. Now, I just need to know how to absorb the unallocated space into my Ubuntu partition. When I go to resize that partition it is not showing the twenty extra GBs I cleared up.

Almost there!!:biggrin:

---

### Post by bodhi.zazen on 2008-07-28
You have to do it in steps. If Ubuntu is in an extended logical partition, you need to resize the extended partition then add to the Ubuntu logical partition.

NOTE: I find the partition resizing tools on Vista are quite blunt ...

---

### Post by Ingenue on 2008-07-28
Thanks everyone for your help. I was able to resize the partitions with the liveCD PartedMagic.

---

### Post by DGortze380 on 2008-07-28
> **Ingenue said:**
> Thanks everyone for your help. I was able to resize the partitions with the liveCD PartedMagic.

Glad you're all set. Please mark the thread as SOLVED through the thread tools menu.

---

### Post by Ingenue on 2008-07-29
Oky doky. Didn't know, sorry for the faux pas.

---

