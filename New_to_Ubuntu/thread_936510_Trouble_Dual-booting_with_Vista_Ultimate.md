---
title: "Trouble Dual-booting with Vista Ultimate"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Madman6510 on 2008-10-02
I want to dual-boot my new PC with both Vista (was already on and paid for, no reason to delete it), and Ubuntu.

When I boot the installer, it gets to the partitioning, where it used to give me an option of both OSes, but for some reason couldn't partition the drives, but now it doesn't recognize that Vista is installed, and only gives me an option to use the entire disk, and manually partition (and it won't let me shrink the NTFS partition with the manual partitioner, either).

And when I try to shrink the partition with the Vista partitioner it just gives me an "Access is Denied" error (hence me wanting to use Ubuntu, lol).

---

### Post by bumanie on 2008-10-02
There is a disk partitioner within vista that will allow you shrink the partition it is on. I have done it myself, but don't use vista on a regular enough basis to remember all the steps, but I think it as follows. Go to my computer, right click; choose manage and then choose manage disks. Right click on c:\ and you should be given the option to shrink volume. After vista is shrunk, you should not have any trouble installing ubuntu as the space given up by vista should be unallocated and you can format this to ext3 with gparted. You can either use the gparted off the live ubuntu cd or download gparted from [here]("http://gparted.sourceforge.net/download.php")

---

### Post by OnlyAwesome on 2008-10-02
Hey.
I found a pretty informative Article on this Website.

[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

Hope this helps!

---

### Post by Madman6510 on 2008-10-02
Doing that just gives me Vista's "I'm too lazy to do it" error, AKA the access is denied error.

EDIT: Also, the text based partitioner doesn't work either, still an access denied error.

---

