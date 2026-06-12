---
title: "[SOLVED] re post, still not sure how to partition a fresh install of ubuntu 8.10"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-11-17
I had to re-post this, cause one of my early replies was misleading everyone else on my thread and manipulated my question into something completely different from my previous question. It made my thread redundant and unhelpful. ;(

I'll have to clarify this.

hello, i have a dell mini 9 and it has an 8 GB SSD.

I want to format my original dell's custom Ubuntu edition.

and install the latest Ubuntu 8.10. I have also made a USB flash drive bootable with Ubuntu 8.10 from Unetbootin. Which I am going to be installing from. 

I am also going to use this online guide help from :

[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

if you can click on that webpage and Scroll down until you see
the Select your country and time zone, and the Select your keyboard layout section.

below it, it has the "Prepare disk space. Preparing the partition part. Before it begins to install the entire operating system. That is the part I am confuse about.

Making one partition for the OS and the other partition for the /home - which i have no idea what this is.

and also this:
dev/sda 
dev/sda - ext2 
and free space

but i don,t understand that jargon of partitioning it.
and leaving how much memory space for two partition and free space. it is rather confusing me.

I just want to install ubuntu 8.10 and leave the rest of the memory to just use for docs, and data.

can someone explain this for me?

(btw, the person who wrote the online guide has a 16 GB SSD. I would of just copy his style of format and I would not ask this forum for help. but since i have an 8 GB SSD. Mines is somewhat different from this guide for partitioning.)

---

### Post by eternalnewbee on 2008-11-17
> Making one partition for the OS and the other partition for the /home - which i have no idea what this is.
You can compare it with drive c, where windoze is installed, and drive d, where you keep your personal data.

---

### Post by cariboo on 2008-11-17
If the device is already partitioned, why not use the existing partitions, then there would be no confusion. 8Gb is not a whole lot of storage space, a normal Ubuntu installation takes between 2 and 3.5Gb. That includes all the extras you need to install, to enjoy your new installation.

Jim

---

### Post by PierreDeKat on 2008-11-17
I think, with only 8 gb to work with, I would skip the separate /home/ partition altogether. I certainly wouldn't go with a 1 gb /home/ because you're going to be totally suffocated there.

Like, if you need to drop an ISO for an installation cd on your desktop, that's 700 mb right there. Do you have room for it?... Hmmm ... Let's right-click on your home partition and see if it's still under 300 mb...

You get the point.

Let your /home/ directory breathe inside that 8 gb partition, and you'll be a lot better off.

---

