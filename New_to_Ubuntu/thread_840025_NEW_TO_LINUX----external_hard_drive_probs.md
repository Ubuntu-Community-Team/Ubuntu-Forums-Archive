---
title: "NEW TO LINUX----external hard drive probs"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by climb.colorado on 2008-06-25
Hey,

Just wondering if someone could answer simple question.  I'm running Hardy - if that matters or not - and when I plug in my external hard drive it mounts properly, but I cannot copy anything to it nor take stuff off.  It has been formatted to ext3.  What's up!?!

Also, does anyone know a good site for games to download?  I'm just trying to get used to Linux and thought installing a few games might help out just a bit.  THANKS!

---

### Post by iaculallad on 2008-06-25
Try to post your /etc/fstab file (with your external drive connected):

```
cat /etc/fstab
```

And do post the output of:

```
sudo fdisk -l
```

---

### Post by climb.colorado on 2008-06-25
> **iaculallad said:**
> Try to post your /etc/fstab file (with your external drive connected):

```
cat /etc/fstab
```

And do post the output of:

```
sudo fdisk -l
```

Here is what I have when it is plugged in:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d1cfbebb-5cf1-429d-a996-50fd8b1568bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=77f15837-b4a5-49ca-97bd-86352f4415b2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


This is what it says with "sudo fdisk -l"


Disk /dev/sda: 137.4 GB, 137438953472 bytes
255 heads, 63 sectors/track, 16709 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11611    93265326    7  HPFS/NTFS
/dev/sda2           16309       16709     3221032+  82  Linux swap / Solaris
/dev/sda3           11612       16308    37728652+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x086a29ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        7296    58597087+   f  W95 Ext'd (LBA)
/dev/sdb5               2        7296    58597056   83  Linux


Thanks again!

---

### Post by gtdaqua on 2008-06-25
Open Terminal application. Type those commands in the command line. See the attached pic.

[IMG]http://www.roominside.com/usbadslmodem/term.png[/IMG]

---

### Post by iaculallad on 2008-06-25
> **climb.colorado said:**
> Still unsure what you mean...sorry, I'm an extreme beginner!  All I really understood is that the code needs to be typed into the terminal - but when exactly?  Please excuse the ignorance.  Thanks again!

Ok. Click on Applications->Accessories->Terminal, next thing to do is issue the commands:

```
cat /etc/fstab
sudo fdisk -l
```

one at a time. On every output of the command, try to copy and paste it in your Ubuntuforums message box.

---

### Post by ad_267 on 2008-06-25
Most games are available in the repositories. Give this a read: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Then if you like first person shooters get nexuiz, alien arena or tremulous.

You can enter stuff into a terminal by going to applications - accessories - terminal. Type the line and hit enter. Then select the output and middle click in the reply box.

---

