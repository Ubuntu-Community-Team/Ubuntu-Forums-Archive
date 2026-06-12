---
title: "accessing documents on HDD"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by jessashe on 2012-03-17
Hi

I woke up this morning and windows 7 did not work (installed an update yesterday and so assume it's something to do with that...) 

That aside, I have installed ubuntu using a bootable USB, and I need to access some coursework which I had saved through windows.  I have read about others partitioning before installing, but since I didn't have a working OS at the time, I haven't been able to do this.  

Do I need to partition, if so how would I do this?

Is there any way of accessing documents created/saved through windows via ubuntu?

please bear in mind that windows is not working (to the extent that I need to back-up my docs and re-install (or remove!))

Thanks a bunch :)

---

### Post by roger_1960 on 2012-03-17
Hi

Well, you may be OK, but maybe not...

When you installed Ubuntu, how did you do it?  It is a live "install" ie running from the USB drive but not written to the hard drive

or

is it installed alongside windows

or

is it installed using the whole disk?

If you run the file manager in Ubuntu by pressing

ctr+alt+T

then type

```
nautilus
```

You should see under "devices" a file system which is your windows partition.  If "devices" is not visible, select "view" then "places".

Let us know what is there.

---

### Post by chipbuster on 2012-03-17
Ahh, Windows. First they have a giant vulnerability that lets anyone execute code on your computer, then the patch crashes stuff.

To install Ubuntu to your hard drive, yes, you do need to partition. You can always use the LiveCD to work on stuff though, since repartitioning disks _always_ carries a risk of data loss.

Ubuntu comes equipped with a tool called ntfs-3g that allows it to read and write off of Windows drives, so if you have a backup drive (an external HDD or USB), pull your files off with the LiveCD (the thing you get when you select "Try without installing"). Then you can partition and install, or just nuke Windows if you feel like it ;)

---

