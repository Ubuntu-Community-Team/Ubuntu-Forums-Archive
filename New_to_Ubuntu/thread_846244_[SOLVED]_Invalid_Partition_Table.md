---
title: "[SOLVED] Invalid Partition Table"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-07-01
I recently decided that enough was enough and deleted my Vista partition using Gparted. Then I resized my ext3 partition to fit the whole hard drive. However, when I rebooted this weird message comes up saying that I have an "Invalid partition table". I tried to restore grub but that was no good. I have no idea what to do. Does anybody have any ideas. Thanks.

---

### Post by uberlube on 2008-07-01
is it possible to get to a command line and show what your partition table looks like.

Use this command:

sudo fdisk -l

---

### Post by uberlube on 2008-07-01
If you cannot even get past grub I recommend you use Partedmagic. It is the best partition editor/ system recovery CD Ive ever used. You can grab it from here:

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

For the future I also recommend that if you want to edit/resize partitions dont do it while you are in your in your main DE and all your partitions are mounted. Use a live CD like Partedmagic and work from within that.

---

### Post by Promaster91 on 2008-07-01
Here is the output of sudo fdisk -l.
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe009e079

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1       30401   244196001   83  Linux

```

---

### Post by Promaster91 on 2008-07-01
No. I used the Gparted live CD not the utility you can run in ubuntu.

---

### Post by jamewill on 2008-07-01
there is a utility called testdisk which will sort your partition table in seconds...

sudo apt-get install testdisk 

or there is a live CD (called "Rescue CD") which you can download

if, however, you have basically a clean drive then whats to stop just reformatting the whole drive and installing from scratch...

jw

---

### Post by bumanie on 2008-07-01
When altering partitions, it needs to be done via a live cd on unmounted partitions. Have a look at [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"), it can rewrite your partition table. But read the documentation carefully first. As far as I know the partition table is written to the first 512 byte sector of the hard drive. I don't think fdisk -l will be helpful in this case.

---

### Post by Promaster91 on 2008-07-01
Ok. I will try this testdisk.

---

### Post by Promaster91 on 2008-07-01
Ok. I have the Partition Magic CD in that has testdisk. What should I do?

---

### Post by Promaster91 on 2008-07-01
Ok. I think I have a bigger problem. I was able to write the partition tables successfully. However, I get a "Error loading operating system." Grub did not load so I will try to restore it now but if anybody has a solution to this problem I will gladly accept feedback.

---

### Post by bumanie on 2008-07-01
If it is just a problem of reinstalling grub. Boot with the ubuntu live cd. in terminal > sudo grub> find /boot/grub/stage1This will give and output of (hdax,x)In the next steps replace the x's with the appropraite numbers. > root hdx,x) > setup (hdx) > quit then try rebooting and see if grub loads. If not, look [here]("http://users.bigpond.net.au/hermanzone/p15.htm") for more info on grub

---

### Post by Promaster91 on 2008-07-01
Unfortunally, I tried that and it did not work. If worse comes to worse I will have to reinstall Ubuntu. Can anyone point me to a good backup how to.

---

### Post by Promaster91 on 2008-07-01
Hey! I got grub to load. However, It still shows that vista is installed. When I try to load ubuntu it says "Error 22: No such partition." How do I upgrade grub menu.lst file?

---

### Post by logos34 on 2008-07-01
Is linux still sda3?  (fdisk)

you might try writing grub to the bootsector of the root partition:

use the same commands above except 
[B]
setup (hd0,[COLOR=Red]2[/COLOR])[/B]

---

### Post by Promaster91 on 2008-07-02
I got it working!!! I just switch the hd(1,X) to hd(0,X). Thanks for everybody's help.

---

