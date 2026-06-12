---
title: "Formatting hard drive through live CD ?"
date: 2006-09-26
forum: Other OS Talk
---

### Post by weasel fierce on 2006-09-26
A friend of mine has a computer thats badly messed up, they are unable to reformat through their normal stuff. I was thinking, is it possible through something like knoppix, to reformat the hard drive, so that it could be then reformatted to windows ?

If so, how would I go about it to do it all, mount the hard drive as read, and format the whole deal correctly for her ?

cheers!

---

### Post by K.Mandla on 2006-09-26
> **weasel fierce said:**
> A friend of mine has a computer thats badly messed up, they are unable to reformat through their normal stuff. I was thinking, is it possible through something like knoppix, to reformat the hard drive, so that it could be then reformatted to windows ?

If so, how would I go about it to do it all, mount the hard drive as read, and format the whole deal correctly for her ?

cheers!
If you just want to blank the drive so you can repartition it and start over, try [Killdisk]("http://www.killdisk.com"). It's free and resets the entire drive to zeroes.

---

### Post by weasel fierce on 2006-09-26
that looks handy. Need to check if that computer has a floppy drive though.

---

### Post by alcamus on 2006-09-26
If I correctly understand what you are asking, you might try booting the Ubuntu live CD and starting gparted from the terminal. It will give you a graphical representation of the drives on your friend's computer and allow you do delete existing partitions and reformat them in a number of different ways, including FAT, FAT32 and NTFS.

Good luck!

As an afterthought, there is also a gparted live CD that is a smaller download and does the same thing. Very handy tool to have around. It is available at the [gparted Sourceforge site]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=446881").

---

### Post by weasel fierce on 2006-09-26
What format do I need to make the partition in, in order for the computer to be able to later install windows on it without trouble ?

---

### Post by K.Mandla on 2006-09-26
> **alcamus said:**
> If I correctly understand what you are asking, you might try booting the Ubuntu live CD and starting gparted from the terminal. It will give you a graphical representation of the drives on your friend's computer and allow you do delete existing partitions and reformat them in a number of different ways, including FAT, FAT32 and NTFS.
That's actually a really good idea too. I was going to suggest booting into an Ubuntu live CD (or any live CD really), opening a terminal and ...

```
sudo fdisk -l
sudo shred -n 1 -v -z /dev/hdXY
```
and then running cfdisk to repartition it, and mkfs to reformat. But alcamus's suggestion is much more fun.

And a lot less gobbledygook! :D

---

### Post by K.Mandla on 2006-09-26
> **weasel fierce said:**
> What format do I need to make the partition in, in order for the computer to be able to later install windows on it without trouble ?
Probably FAT32 for Win98/Me or earlier. NTFS for Win2K or later. What system to you want to install? Win2K and XP will allow you to format the drive as part of the installation, but I don't remember about 95/98/Me.

---

### Post by K.Mandla on 2006-09-26
> **weasel fierce said:**
> that looks handy. Need to check if that computer has a floppy drive though.
It'll run off CD too, or USB drive if your computer will boot from USB.

---

### Post by weasel fierce on 2006-09-26
Its win2K, and so far, trying to format from her install CD has proven unsuccessfull. Im not sure yet if it may be the CD, but I figured I'd give it a shot clearing the partition alltogether, and then going from there.

You guys are the bomb, btw

---

