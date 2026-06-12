---
title: "Moving from Fedora to Ubuntu RAID 5 issue"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by blackjackjester on 2008-07-12
Hello everyone,

A little background:

I had previously had a RAID 5 array consisting of 4 500GB drives set
up using mdadm in Fedora 7.  This worked pretty good, but I wanted to
move it over to Ubuntu, and since 8.04 is pretty new, I figured it was
a good time.  I also just like tooling around with this computer, as
there wasn't a real need to switch it other than 'I wanted to'.

But anyways, I backed up all the data on the RAID, and installed
Ubunutu.  I'm attempting to set up the raid again from scratch (I
briefly looked into reassembling it using mdadm, but after about 30
minutes, I figure I can just start from scratch).

Initially, the only drives visible from gparted were the 4 500gb ones
and the 80gb one the OS is installed on.  After individually deleting
all the partitions on them, the old RAID /dev/md0 showed up with the
1.36TB showing as unallocated.  I'm not sure why this is - maybe mdadm
built a config file...not sure.

Anyway, now when I try to format the 1.36TB of unallocated space, I
get a "A partition cannot have a length of -1 sectors" error.  Not sure 
exactly what this means and how to fix it.  I also don't know how to start 
the raid from scratch and get rid of md0, possibly a config file I need 
to edit that I'm not sure where it is.

The base question here is : How do I format this 1.36TB md0 to ext3?

Thanks for any help.  I'll try to answer questions if there are any.

---

