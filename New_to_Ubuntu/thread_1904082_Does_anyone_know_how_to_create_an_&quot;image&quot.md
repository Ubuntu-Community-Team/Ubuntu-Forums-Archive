---
title: "Does anyone know how to create an &quot;image&quot; of a floppy disk in Linux?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2012-01-04
Hi, 

Does anyone know how to create an image file of a floppy disk in Linux?
I have a floppy disk (and a floppy drive) and I would like to create an image file of the diskette onto my hard drive.  There are several programs in Windows that can do it, but I can't figure it out in Linux.  I think it is called a "raw" image and I think it needs to be in the ".img" format.

The only thing I have come up with is "dd", but I don't really understand it.  I also came across DOSemu, but couldn't really figure out how to do it that way either.

Can anyone hep me?

I'm running Ubuntu 11.04

---

### Post by 1clue on 2012-01-04
Try **man mkdosfs**

*Edit:*...in a terminal window.

---

### Post by bcschmerker on 2012-01-04
Actually, a Disk Image is a completely different kind of creature from a photograph.  Philips® Compact Disc&#8482; Data Storage, Digital Versatile Disc&#8482; Data, and Blu-ray® all use the ISO 9660 file format, often as large single files recognizable by the .iso tag on the filename.

Disquettes in the 3.5" and 5.25" sizes on most microcomputers applicable to LinUX use an older type of filesystem:  the File Allocation Table system developed by Microsoft and initially used in International Business Machines® Personal Computer&#8482; DOS (1982), which places a file-allocation table and a directory on Track 0 after the boot sector; disquette images are raw object code and data (in blocks of 512 bytes) in the .img file format.  GNU® MTools (package: mtools) provides mpartition (Amend FAT Device Partition Table), mformat (Format FAT Media), mcopy (Copy FAT Image) and mdel (Delete FAT Image).  In UDevFS, the disquette drives are normally located starting at /dev/fd0.

---

### Post by HermanAB on 2012-01-04
Just use the good old kitty:
$ sudo cat /dev/fdo > floppyimagefile

---

### Post by anewguy on 2012-01-04
It's been a while since I used a floppy, and I don't have one on any of my computers.  But.......the following *might* work but I have no way to test it.

First you need to create a folder to mount the floppy to:

mkdir ~/floppy

Second, mount the flopy to the folder:

sudo mount /dev/fd0 ~/floppy  (I don't remember now if there are other parameters to put in here if the disk was formatted for Linux versus DOS/Windows, and hence why I'n not sure if a cat of the disk will work for non-linux disks - I've just never tried it, so I'm disagreeing with HermanAB).

Third, see if the floppy shows as a mounted device.  If so, right-click on icon for the drive, select copy disk, then make the output a file (iso).

Not real sure on this, but I think there is a copy disk option on the right-click menu.

Let me know if that does anything (you can't hurt anything).

Dave ;)

---

### Post by lkraemer on 2012-01-04
To mount a USB Floppy in Debian "Squeeze" I use:
```

sudo blkid

```
which gives:
> 
/dev/sda1: UUID="3146c670-3d45-47bf-b4b8-f89b7e0c9398" TYPE="ext3" 
/dev/sda5: UUID="2d6939e4-3542-4721-a6b0-e50e6c81ae88" TYPE="swap" 
/dev/sda6: UUID="b926c410-0302-4ffa-8ca6-bd714a1d6238" TYPE="ext3" 
/dev/sdb: SEC_TYPE="msdos" UUID="2113-1602" TYPE="vfat"
 
Now, I know where the Floppy is ......

To MOUNT the floppy, you may need to create the mount point, and the
subdirectory where it mounts....Typically it is mounted at /media/somesubdir where somesubdir is your choice......or /mnt/somesubdir
```

udisks --mount /dev/sdb

```
Mounted /org/freedesktop/UDisks/devices/sdb at /media/2113-1602
```

dd if=filename of=/dev/sdb bs=1024 conv=sync ; sync

```
to umount the floppy:
```

udisks --unmount /dev/sdb

```


Format a Floppy:
```

fdformat /dev/sdb

```

Copy 3.5" Floppy to img file:
```

     dd if=/dev/fd0 of=floppy.img count=1 bs=1440k 

```

Copy img file to 3.5" Floppy:
```

     dd if=floppy.img of=/dev/fd0 count=1 bs=1440k

```

Larry

---

### Post by anewguy on 2012-01-04
Thanks Larry!  I'm keeping this bookmarked as I have friends using Ubuntu who do use floppies, and I sure sooner than later this is going to come up.  Great to have nice reference to refer to!

Dave ;)

---

### Post by 1clue on 2012-01-04
> **HermanAB said:**
> Just use the good old kitty:
$ sudo cat /dev/fdo > floppyimagefile

That works only if you have a floppy to make an image of.

Oh, heck I just read the title of the thread.  You're absolutely right.

---

### Post by HermanAB on 2012-01-04
I think there was a competition for gratuitous uses of 'cat'.  It is amazing what you can do with it.

---

### Post by 1clue on 2012-01-04
No, I use it like that all the time for CDROM images.  I misunderstood the question originally, I thought you were making a *new, blank* image instead of copying a floppy.

Although frankly this thread is a bit bizarre for me.  It's like "Does anyone know how to make punch cards?"  Sorry but I haven't had a floppy in a computer I owned for at least 8 years.  I'm surprised they still make them.  CDROM blanks are so cheap now, or use a USB stick.

---

### Post by 1clue on 2012-01-04
Another super-handy gratuitous use of cat would be:

cat /dev/null > /some/other/file

This zeroes the file without needing to close it in other apps.  For example, if you have a web server log you can zero it out without shutting down the server.  The open file pointers just go back to zero and start from there.  It's what logrotate uses I think, they back it up and then zero it out.

---

### Post by Learning Linux 2011 on 2012-01-04
I'm the original poster.

I'm not looking to format a floppy, I have some old floppy disks that I am trying to make image files of and put them on my hard drive.  They use the FAT format (I guess I should've specified that).  They are also bootable (DOS?) floppies.
I'm making them for use with VirtualBox or something similar, which seems to require bootable floppy *images*, rather than the actual floppy disks themselves. Images are much easier to deal with anyway.

It occurred to me that I didn't know how to do it using Linux.  There are several ways in Windows though that are very easy.  I just don't have Windows installed at the moment.  I have VirtualBox with Windows, but the floppy won't show up in the VirtualBox and they won't accept booting from an actual floppy disk drive anymore, even though I swear that worked in the past.

Incidently, my floppy drive is internal, rather than USB.

So far the MTools seems to have worked (I never knew about those, they are ultra cool)
and the sudo cat command seems to have worked.  MKDOSFS does seem to be just for formatting.

I'll try the others when I have the time.

---

### Post by anewguy on 2012-01-05
> **1clue said:**
> No, I use it like that all the time for CDROM images.  I misunderstood the question originally, I thought you were making a *new, blank* image instead of copying a floppy.

Although frankly this thread is a bit bizarre for me.  It's like "Does anyone know how to make punch cards?"  Sorry but I haven't had a floppy in a computer I owned for at least 8 years.  I'm surprised they still make them.  CDROM blanks are so cheap now, or use a USB stick.

Punch cards?  Try a flood going through your data center and youre called in to work on the mainframe, only to find the entire backplane full of the punches - millions of them - the ran in the flood water after it hit the hoppers on the card punchers.  

Wow, I'm REALLY showing my age now!!

EDIT:  I forgot to mention - yep, I know how to make punch cards.  You find a really ugly holiday/birthday/whatever card, beat it to a pulp and there you have it - a punch(ed) card.   Okay, that was bad, but in my minds eye it's still weird enough to be funny ;)

Dave ;)

---

