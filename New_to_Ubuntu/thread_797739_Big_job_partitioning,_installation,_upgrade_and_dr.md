---
title: "Big job: partitioning, installation, upgrade and drivers"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by eeeandrew on 2008-05-17
I've now been running ubuntu 7.04 since last September dual boot wiht windows Vista. I've decided to remove Vista and go solo linux. I've read on this forum that ideally the root and home should be on seperate partitions but mine are all in the same partition. So my to-do list looks a little like this:

1)Remove Vista
2)Get root and home onto seperate partitions
3)upgrade to either 7.10 or 8.04

When I first installed 7.04 I had difficulty getting both my wifi card and sound card running. Both of these issues were eventually fixed with help from this forum. The sound card driver was missing a line of code and the wifi card had to be run under ndiswrapper.

So my questions are.

1)whats the easiest way to move home and root onto seperate partitions without losing my data?
2)whats the best way to take the blank space formally occupied by vista and use it for linux
3)if I upgrade to 7.10 or 8.04 through the "update" option in the update manager will my sound and wifi card still work?

---

### Post by volkswagner on 2008-05-17
> **eeeandrew said:**
> 
So my questions are.

1)whats the easiest way to move home and root onto seperate partitions without losing my data?
2)whats the best way to take the blank space formally occupied by vista and use it for linux
3)if I upgrade to 7.10 or 8.04 through the "update" option in the update manager will my sound and wifi card still work?

I would burn 8.04 of your choice.  Boot live cd.  When running the live cd, you will be able to see how well your hardware is supported.  

Delete windows partition, using partition manager from live CD.  Create two new partitions, one for / , and one for /home.  Size accordingly.  You can keep /home small just for config files and such.  Or make it large for config, and data.

You can then run the install for 8.04 on the desktop.  Use guided partition and select your new partitions and mount points.  You can use your existing swap partition.

After reboot you can move your old files from /home to your new /home partition.  You should only need to move some files.  You will want your Bookmarks for firefox, old email, address book, mail config, etc.  Once you have a fully functional system you can delete 7.04 when you are ready.  Use the new space for data, or a new distro you want to try.

A clean install is usually preferred when possible.

---

