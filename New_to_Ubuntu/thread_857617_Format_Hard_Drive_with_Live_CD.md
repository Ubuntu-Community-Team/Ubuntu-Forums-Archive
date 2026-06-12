---
title: "Format Hard Drive with Live CD?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by kittykatmeowmeow on 2008-07-12
How do I format my C Drive with the Ubuntu 7.10 Live CD? My ultimate goal is to wipe the drive and try to boot it with Vista Recovery and then create a second partition for the Ubuntu program.  But first..I need to know how to format the C drive with Ubuntu.  Please help!:confused::confused::confused::confused:

---

### Post by TSS on 2008-07-12
I suggest you use GParted LiveCD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)), a LiveCD especially made for partitioning tasks. It's possible with the Ubuntu LiveCD, but GParted is easier.

If you are trying to make space for Ubuntu, why not just shrink the partition using Vista ([http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)?](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)?)  After you have some free space, the Ubuntu installer will get the job done.

1.) Shrink Vista partition using Vista
2.) Run Ubuntu installer and let it create partitions in the newly freed space

---

### Post by WRDN on 2008-07-12
If I understand properly, it sounds like you already have Vista installed. If so, you can use the disk partitioner to resize Vista's partition, which you can then install Ubuntu on. Its also possible to do this process using GParted on the LiveCD.

If you want to format it though, just delete all partitions you want in GParted (System > Administration), by selecting them and clicking Delete. You can also use GParted to format them to the filesystem you want.

---

### Post by kittykatmeowmeow on 2008-07-12
Thank you very much!  I was able to reformat my hard drive by deleting the partition, but not allocating it to anything.  I was also able to pull up my computer's Vista recovery :)  I feel so much better....even if I did loose about 100 GB worth of data :(  Note to anyone that uses Vista...Do NOT turn off the system during a windows update....you will get the BSOD!!

HORRAY FOR UBUNTU!

---

