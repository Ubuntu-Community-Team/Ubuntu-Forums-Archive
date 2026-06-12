---
title: "Question about Mount Point in installation of Ubuntu"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by E-babe on 2008-04-28
As captioned above, I have no idea what a mount point is because i have just made the transition from windows to linux. So i have set my partition like below:

sdb1 - /     - 100gb
sdb2 - /home - 140gb

So what're mount points really? i see there are others like /user, /boot,..etc
And is there a problem with my setup above? Thank you very much for any help.

---

### Post by bluefrog on 2008-04-28
to make it very simple, consider / and /home as your C and D in windows.

100 Gb for / being a bit big, 10 Gb would be more than enough for normal use.

---

### Post by E-babe on 2008-04-28
> **bluefrog said:**
> to make it very simple, consider / and /home as your C and D in windows.

100 Gb for / being a bit big, 10 Gb would be more than enough for normal use.
can you tell me a bit about each of the other ones... such as /boot, /usr.... etc
it's strange how the hard drive is divided up

furthermore, if i wanted to redo it your way (10gb)... that means i have to re-paritition my / drive right?

---

### Post by houstonbofh on 2008-04-28
Unix has a single file tree structure.  It starts with the root, or '/' which is the top of the system.  If you have a single drive, everything is under it, and it looks a lot like Windows without the drive letter.  Now you want to add a new drive (or partition) so you "mount" it somewhere in the file system.  There are a few places that are traditionally common, like /boot and /home, but it could be anything like /home/owner/Desktop/ExtraPics/vacation which would give you and entire partition as "vacation" in your ExtraPics directory on your desktop.

Generally I just use one partition, as it is easier to manage drive size.  A lot of people use a separate /home partition to make reinstalls simple.  Your config is already there.

---

### Post by houstonbofh on 2008-04-28
> **E-babe said:**
> furthermore, if i wanted to redo it your way (10gb)... that means i have to re-paritition my / drive right?
You can boot the Live CD and use gparted to resize your partitions.

---

### Post by Zimmer on 2008-04-28
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
This article helped me understand mount points..

---

### Post by E-babe on 2008-04-28
Thank you guys for all your help!

---

### Post by E-babe on 2008-04-28
> **houstonbofh said:**
> You can boot the Live CD and use gparted to resize your partitions.
So i used your method and gparted out 10gb of space for / volumn
now my question is.. how do i attribute that 90gb of space to a specific place like /home or /boot or /whatever???...
I have created this new partition, but it only shows in my computer as a new drive and i want it to root in my / directory

Another question is how do i rename my drivers.. like the default name for / is "filesystem" but i don't have the permission to do that.

i am such a noob at linux...

---

### Post by houstonbofh on 2008-05-11
The lable "filesystem" is not a name, it is what it is.  It is your filesystem.  As to mounting, this is a good walkthrough.
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

