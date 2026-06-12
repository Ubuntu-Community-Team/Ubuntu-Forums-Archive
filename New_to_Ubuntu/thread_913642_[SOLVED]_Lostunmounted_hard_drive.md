---
title: "[SOLVED] Lost/unmounted hard drive"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by karindalziel on 2008-09-08
Last week I installed a new 250 GB seagate HD on my Ubuntu machine, running 8.04. I mostly followed the instructions on this page: 

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

with some help from this page: 

[http://www.linuxquestions.org/questions/linux-newbie-8/having-problems-mounting-hd.-mount-you-must-specify-the-filesystem-type-188956/](http://www.linuxquestions.org/questions/linux-newbie-8/having-problems-mounting-hd.-mount-you-must-specify-the-filesystem-type-188956/)

Anyway, I got everything working fine, and mounted the drive at /media/storage. I copied a bunch of stuff to it, could access it from external computers, etc. 

Today, while changing a bunch of stuff on my computer (mostly compiz and screenlet related) I lost the hard drive. I tried undoing everything I'd done to no avail. At first I thought everything was lost on the drive, but it doesn't show up when I run 

```
sudo lshw -C disk
```

or 

```
df -h
```

I checked the sata connection cable and the power to the drive. I suppose the drive could have just died, but I don't know how to test for that- and I think it's unlikely since it's brand new. 

Is there a way to "find" this drive again?

---

### Post by alienexplorers on 2008-09-08
Post the output of 
> df -h
and
> sudo fdisk -l
also from your terminal post the output from this command:
> cat /etc/fstab

---

### Post by karindalziel on 2008-09-08
df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              32G  3.4G   27G  12% /
varrun                1.5G  236K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   48K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   39M  1.5G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3             190G  130G   51G  73% /home

```

sudo fdisk -l

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4155    33375006   83  Linux
/dev/sda2           29259       30394     9124920    5  Extended
/dev/sda3            4156       29258   201639847+  83  Linux
/dev/sda5           29259       30394     9124888+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9fcadce3-20a9-43f8-bf53-5c2e866a25b2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=934399e6-67d9-47e5-a369-3010570c0052 /home           ext3    defaults        0       2
# /dev/sda5
UUID=19483f34-42a0-41df-a70f-bf77a1215309 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

So, judging from sudo fdisk -l the drive is there but has no valid partition table? I'm hoping not to have to reformat the drive (though I can if need be).

Oh, and one more bit of info- when I formatted the drive last week, I used ext3.

Thanks for your help!

---

### Post by alienexplorers on 2008-09-08
It looks like you will need to reformat /dev/sdb to repartition it.

---

### Post by karindalziel on 2008-09-08
Damn. I was afraid of that. 

OK, what I'm more concerned about right now, does anyone have any idea what I might have done to cause this? Losing the data sucks, but now I'm not sure I can trust the drive. It might just be that the drive is bad. 

boo. 

Thanks for your help, though!

---

### Post by karindalziel on 2008-09-08
OK, weirdness! I just noticed a 250 gig drive in my nautilus sidebar, clicked on it, and lo and behold, my missing drive!  (it asked me for my password before I could access) Still get the same errors otherwise- this appears to be the ONLY way I can access the drive. Can't mount it back in its old location, either. 

[IMG]http://farm4.static.flickr.com/3045/2841876946_10ee583725.jpg[/IMG]

Now I am super confused, but at least I have my data. :confused: (and yes, it's only video I thought I lost, which is why I wasn't too concerned.)

Edit - drive is showing up again when I run df. I suspect a buggy drive.

---

### Post by drs305 on 2008-09-08
Is this an internal or external drive? 

You don't have an fstab entry for it, which is normal for an external drive. If it's internal or you always want it mounted, you can do it through fstab. An entry for an internal drive would be very easy. For an external, I'd recommend labeling the drive, whether you put it in fstab or not.

---

