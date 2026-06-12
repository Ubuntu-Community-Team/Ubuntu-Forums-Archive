---
title: "Problem after restarting Ubuntu"
date: 2015-01-10
forum: New to Ubuntu
---

### Post by davidlubomirov on 2015-01-10
Hello, 

currently I'm using Windows 7 and Ubuntu 14. Here is my problem. I use Easy BSD for dual boot, and after restart on my Linux and tried to start it again here is what I get:

[B]Try (hd0,0): non -MS: skip
Try (hd0,1): EXT2: [/B]

Windows 7 works fine and there are no problem starting and working whit that OS. 

My question is how can I recover my files or at least start Ubuntu to copy them?

Thanks in advance. :)

---

### Post by TheFu on 2015-01-10
You can boot off any live CD or live flash drive with Ubuntu or any other distro that you like, then mount the linux partitions (assuming no encryption) and copy the files anywhere you like.
Of course, already having a backup would be ideal. Please get backup religion sooner than later.

If you want to try to fix the issue, the boot-repair distro might be the shortest way to a solution. I assume since you use an alternate boot tool, that you are familiar with the other options. My signature has links.

---

### Post by davidlubomirov on 2015-01-10
I already try booting fron live CD but when I tried copying the files everything crash. Any idea why? And can you give me any suggestion for the booting distro?  :)

---

### Post by TheFu on 2015-01-10
Distros to try:
Ubuntu
Mint
Fedora
rescuecd
Debian
TinyCore
DSL
any of 50 others.

Basically any of them that boots and has enough of an OS to mount whatever file system the files are stored under AND will let you push those files somewhere else over the network.

Did you happen to try boot-repair?

---

### Post by davidlubomirov on 2015-01-10
Yes I try boot-repair but get the same message again. Now I will try Live CD from distro different then Ubuntu.

---

### Post by Mark Phelps on 2015-01-10
Did you intentionally install Ubuntu to an Ext2 filesystem? Asking because, for a long time now, the default has been Ext4.

If the filesystem is actually Ext4, then use the edit option in EasyBCD to edit the boot entries to change Ext2 to Ext4 -- and see if that works.

---

