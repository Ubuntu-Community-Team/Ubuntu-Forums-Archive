---
title: "[SOLVED] is it safe to install ubuntu"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by ercferret18 on 2008-05-27
so now i've tried ubuntu with wubi and decided that i want to install it on a partition. I have windows vista and in the installation i chose the guided-resize windows vista longhorn/bootloader and use free space. my computer is an hp desktop, and hp included a recovery partition to restore the hard drive. i have not yet clicked the install button, however the windows vista partition has already been resized

1)is this safe
2)is my windows vista partition still going to be there (have a lot of files on it)
3)will the recovery partition still be there?

any help appreciated.

---

### Post by sayakb on 2008-05-27
You might need to shrink the Vista partition to create a new partition. In Vista, right click on "Computer" and select "Manage". There, select "Disk management" from the list and shrink the larger Vista partition from there. You may shrink to about 10-15GB for Ubuntu (since you can still access the Vista partition from ubuntu, you might not need much space for data, but for just the ubuntu packages). Leave the unpartitioned space so left out after shrinking. You shall create a new ext3 partition during Ubuntu install.

And what exactly do you mean by "safe". Please elaborate.

---

### Post by Duck2006 on 2008-05-27
This may help.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by ercferret18 on 2008-05-27
> **LinuxIsInnovation said:**
> You might need to shrink the Vista partition to create a new partition. In Vista, right click on "Computer" and select "Manage". There, select "Disk management" from the list and shrink the larger Vista partition from there. You may shrink to about 10-15GB for Ubuntu (since you can still access the Vista partition from ubuntu, you might not need much space for data, but for just the ubuntu packages). Leave the unpartitioned space so left out after shrinking. You shall create a new ext3 partition during Ubuntu install.

And what exactly do you mean by "safe". Please elaborate.

Well it automatically shrinked the vista partition, and what i basically mean by safe is that i want my computer to actually boot (lol), and other partitions to be left untouched (except for the resizing)

---

### Post by sayakb on 2008-05-27
It's better to create a self managed partition rather going for Guided (ie. use manual partitioning). This is because GUided may assign unnecessarily big sizes to Swap partitions. And ofcourse, its 100% "safe".. I used Vista (preloaded) + Ubuntu for a couple of months. Now I got rid of Vista (though the recovery partition is still there) :)

---

### Post by rudeboyskunk on 2008-05-27
Please please please back up all your necessary files before you do anything, though.  Too many people post about how they lost everything during an install or something or other because they didn't back up anything.  Get a USB stick or put it all on a DVD or SOMETHING, but back up your stuff!  Nothing is 100% safe.

---

### Post by inportb on 2008-05-27
> **LinuxIsInnovation said:**
> And ofcourse, its 100% "safe".. I used Vista (preloaded) + Ubuntu for a couple of months. Now I got rid of Vista (though the recovery partition is still there) :)

You can take the next step, dd the recovery partition into a backup image, and get rid of it ;p

---

### Post by JustAnotherVagueAnon on 2008-05-27
Yes, your situation sounds like mine exactly. I started on wubi, loved it, and decided to actually partition my desktop using the ISO. I also have an HP with a separate partition as backup. Backup everything just to be safe and the live cd should easily guide you through it.

---

### Post by sayakb on 2008-05-27
Yes, Guided might not be 100% safe. So if you shrink beforehand, ubuntu will not touch your Vista partition at all..

---

### Post by Paqman on 2008-05-27
Did you know that you can simply migrate your Wubi-installed copy of Ubuntu to your new partition?

[HowTo use LVPM](http://lubi.sourceforge.net/lvpm.html)

---

### Post by Sef on 2008-05-27
> It's better to create a self managed partition rather going for Guided (ie. use manual partitioning).

1) Before attempting an install **back up** your data.

2) Manual partitioning is not hard, but it is tricky the first time or two.  

3) As has been mentioned, use _Vista's partitioner_ to shrink the Vista partition.

---

### Post by ercferret18 on 2008-05-27
yay it worked!! thx everyone

---

### Post by rjdsmiths on 2008-05-27
The Awnswer to your Question of "is It Safe" is yes, it should be.....But
nothing is perfect especialy in computers (yet!!) so if I were you I would Back Up to disk if there are some totaly essential folders/files

Best of Luck

---

