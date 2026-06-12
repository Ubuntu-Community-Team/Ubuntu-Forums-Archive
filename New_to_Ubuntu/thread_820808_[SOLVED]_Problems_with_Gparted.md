---
title: "[SOLVED] Problems with Gparted"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by MasterSander on 2008-06-06
I messed around a little with gparted, I tried to resize my ntfs partition but I couldn't, so I tried to unmount it, but that didn't help and now I can't even mount it back. 

root@sander-pc:~# mount /dev/sda2
fuse: failed to access mountpoint /media/BOOT: Bestand of map bestaat niet

---

### Post by Duck2006 on 2008-06-06
Did you defrag your win drive first?

Try the live cd of gparted.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by MasterSander on 2008-06-06
No the problem is I don't want it reformated, I tried to shrink it, but I wasn't able to. It still has vista on it which I'll be needing tomorrow to work on.

---

### Post by Duck2006 on 2008-06-06
You windoze drive resize it from within vista, it don't like being resized with any thing other than vista partition tool.

---

### Post by MasterSander on 2008-06-06
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dd51e640-5ab2-4675-8b44-1b9ce6d58daa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=a069ccea-2df3-41f1-9385-b7e7be081564 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda2 /media/BOOT ntfs defaults 0 0

This is what fstab looks like, I figured out that he says he can't find BOOT because there is no /dev/sda2. But how can you get the partition back after being unmounted?

---

### Post by MasterSander on 2008-06-06
Yeah, but it didn't work in Vista either, he couldn't shrink.

---

### Post by Duck2006 on 2008-06-06
Some info on fstab to mount win drives that may help you get it back.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by stchman on 2008-06-06
> **MasterSander said:**
> I messed around a little with gparted, I tried to resize my ntfs partition but I couldn't, so I tried to unmount it, but that didn't help and now I can't even mount it back. 

root@sander-pc:~# mount /dev/sda2
fuse: failed to access mountpoint /media/BOOT: Bestand of map bestaat niet

Vista has it's own shrinking program.

Problem with resizing NTFS partitions is that you need to do the following:

1.  Defrag the partition you want to resize.
2.  Perform a chkdsk /f on all partitions.

Remember NTFS partitions are prone to fragmentation and errors so they must all be fixed before resizing.

Also download the gparted LiveCD from sourceforge.  There is a plethora of NTFS tools on the CD that might be able to fix the problem.  I was able to fix a problem on a NTFS drive with the full gparted LiveCD.

Use this link to download the .iso for the full gparted LiveCD.

[http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-live-0.3.6-7.iso](http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-live-0.3.6-7.iso)

---

### Post by MasterSander on 2008-06-06
Posted before I read.

---

### Post by Duck2006 on 2008-06-06
Try changing this.

/dev/sda2 /media/BOOT ntfs defaults 0 0

to this

/dev/sda2 /medis/BOOT ntfs nls=utf8,umask=0222 0 0

---

### Post by MasterSander on 2008-06-06
I'll try stchman's advise when I got more time, but you're right in my opinion about shrinking ntfs drives. But I still can't mount my ntfs drive, although I've listed it in /etc/fstab and /dev/sda2 does exist.

---

### Post by MasterSander on 2008-06-06
still doesn't work after changing. Try another reboot?

---

### Post by Duck2006 on 2008-06-06
Did you set the mount point?

sudo mkdir /media/BOOT

---

### Post by briandu on 2008-06-06
Reading this I assume u are typing from Ubuntu.

If so just do this in a xterm session 

sudo mount /dev/hda0 /mnt/ntfs      
I assume your Vista is hda0 and u r mounting at folder ntfs

now this will fail!!!! but!!!!! look carefully and it will tell u what to do, look for statement 

mount ............ enad ends with -o forced  -----look carefully it is there, I had same prob

you are forcing vista to overide a vista access lock

when done so you can exit and go back to Vista

---

### Post by MasterSander on 2008-06-06
:P k that worked, thx a lot for your patience and time. I though ubuntu would create that if I mounted.

---

