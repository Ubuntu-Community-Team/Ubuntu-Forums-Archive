---
title: "cannot use dd to create an image of a partition"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by Paul Hartwig on 2012-02-11
command is:  sudo dd if=/dev/sdb1 of=/dev/sdc2.xxx.img
get message that there is no storage space on output file sdc2
sdb1 is a 54 Gb. ext4 partition, my ubuntu 11.10  on external hard drive 
sdc2 is an empty 80 Gb. ext4 partition on another external hard drive
results are the same if devs are mounted or unmounted or if I run it as root

It only works if I use sudo dd if=/devsdb1 of=~/xxx.img wich writes the image file in my user directory,
wich I don't want because it will not fit.

need help, as I am new to Linux....

---

### Post by jerrrys on 2012-02-11
Would a GUI be any help?

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by scradock on 2012-02-11
> **Paul Hartwig said:**
> command is:  sudo dd if=/dev/sdb1 of=/dev/sdc2.xxx.img
get message that there is no storage space on output file sdc2
sdb1 is a 54 Gb. ext4 partition, my ubuntu 11.10  on external hard drive 
sdc2 is an empty 80 Gb. ext4 partition on another external hard drive
results are the same if devs are mounted or unmounted or if I run it as root

It only works if I use sudo dd if=/devsdb1 of=~/xxx.img wich writes the image file in my user directory,
wich I don't want because it will not fit.

need help, as I am new to Linux....

Your command-line is incorrect - try ...of=/dev/sdc2/xxx.img

HTH

---

### Post by Dave_L on 2012-02-11
> **Paul Hartwig said:**
> command is:  sudo dd if=/dev/sdb1 of=/dev/sdc2.xxx.img

Shouldn't that be /dev/sdc2/xxx.img ?

---

### Post by Paul Hartwig on 2012-02-11
have spent hours searching and reading including Ubuntu Ref & Resc, no help.
don*t want to use clonezilla

---

### Post by Paul Hartwig on 2012-02-11
sorry, but when I do that, get message "/DEV/SDC2/XXX.IMG  IS NOT A DIRECTORY

---

### Post by Dave_L on 2012-02-11
Ok. I think you need to mount the destination device sdc2, and then use the mount point in the target parameter.

If sdc2 is mounted at /media/sdc2, then use the command:

sudo  dd if=/dev/sdb1 of=/media/sdc2/xxx.img

I don't have a lot of experience with the dd command, so I'm not certain about this.

---

### Post by The Cog on 2012-02-12
Nice one, Dave_L - I think you've put your finger on the problem. 

@Paul Hartwig: If /dev/sdc2 is not already mounted, these commands will do the trick:
```
sudo mkdir /media/sdc2
sudo mount /dev/sdc2 /media/sdc2
sudo dd if=/dev/sdb1 of=/media/sdc2/xxx.img
sudo umount /dev/sdc2
sudo rmdir /media/sdc2
```

---

### Post by Paul Hartwig on 2012-02-12
Hi all,
created a small test partition so that it doesent take too long.
With this cmd it works:
dd if=/dev/sdb6 of=/media/f7c27536-30e2-40d9-940c-8cdb8f5b465f/disk6.img 

51200+0 Datensätze ein
51200+0 Datensätze aus
26214400 Bytes (26 MB) kopiert, 0,77086 s, 34,0 MB/s

The external hard drive where I want to store my image files is mounted at:
/media/f7c27536-30e2-40d9-940c-8cdb8f5b465f 

Now that I can create images, the next step is restoring them, keep your fingers crossed for me.

---

### Post by The Cog on 2012-02-12
It will be the reverse command:
dd if=/media/f7c27536-30e2-40d9-940c-8cdb8f5b465f/disk6.img of=/dev/sdb6
Be careful to restore to the right partition!

You can mark the thread solved using [COLOR="Red"]**Thread Tools**[/COLOR] at the top of the page.

---

