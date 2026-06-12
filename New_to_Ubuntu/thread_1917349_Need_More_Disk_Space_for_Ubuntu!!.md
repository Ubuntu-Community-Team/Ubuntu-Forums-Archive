---
title: "Need More Disk Space for Ubuntu!!"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by chughes27 on 2012-01-29
So, I set the install size of my Ubuntu to 10GB, thinking I didn't need a whole lot of space for it. Turns out though that I do need more, but I don't know how to resize it.

---

### Post by Bucky Ball on 2012-01-29
* Back up valuable data. 
* Boot from the LiveCD and 'Try Ubuntu'. 
* Open Gparted (partition editor) and shrink the partition next to your Ubuntu install the amount that you want to add to the Ubuntu partition. This will give you a block of free space. 
* Resize your Ubuntu partition to use up this free space. That's it ...

This must be done from the CD and not a running install as all partitions you are manipulating need to be unmounted (obviously not possible if you are running Ubuntu on the partition you want to resize).

Good luck. It's pretty straightforward. 20Gb in total for the Ubuntu partition should be plenty if you have a separate /home partition. If not and you are intending to keep all your personal data inside the / partition I would suggest considerably larger size.

---

### Post by chughes27 on 2012-01-29
Thanks sounds helpful, a pretty big problem though...

My computer has no CD drive, I used the Ubuntu installer so I could run it alongside Windows. Is there a way to do this with this method of installation?

---

### Post by drs305 on 2012-01-29
Not having a CD makes things more difficult but it can be done.

The easiest way would be to create a bootable linux usb drive. You will then be able to use Gparted on your unmounted Ubuntu partition to resize it. (Resize Windows from within Windows first.)

Here is a guide I wrote about resizing Ubuntu while back. Also check out the link at the bottom of the first post for the link to *srs5694*'s post.
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

If you can't make a bootable USB, there is another way, although a bit more complicated.

You can download the Ubuntu iso and then boot it from the Grub 2 command line. Here is a link I wrote about doing that. You would only be booting the ISO via "Try it", not actually doing an installation. 'Try it' will take you to the Ubuntu Desktop, where you can run commands and apps.
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

You can start at the 'load modules' section of Step 3.

This may be more than you want, but it is a workaround when you have nothing but your hard drive.

---

