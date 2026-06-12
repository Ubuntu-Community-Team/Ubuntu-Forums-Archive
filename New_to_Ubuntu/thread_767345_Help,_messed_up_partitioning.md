---
title: "Help, messed up partitioning"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by jdw1584 on 2008-04-25
So during my first install i messed up my partitioning and the amount of space available to split between windows and ubuntu has shrunk during the 2nd try.  now when i do a manual partitioning i have 1 partition w/ 86gb, one with 13 mb, and 150gb of free space.  how do i reinclude that free space in my windowns/ubuntu split for the partitioning?

---

### Post by raul_ on 2008-04-25
Burn the GParted live cd and resize the partitions as you want. Keep in mind that there is always a risk of losing data. 

I think you can also use the partitioner (also GParted) included the in the Ubuntu LiveCd but I just feel safer with the GParted live cd. You can download the iso from their site

---

### Post by jdw1584 on 2008-04-25
should i just turn the free space into a partition or what?

---

### Post by jdw1584 on 2008-04-25
if I'm splitting my hd between windows and ubuntu, do i need 1 big partition and let the thing split them into two or should i create two from the start? cause if i turn the free space into a partition i'd have 3, so would it just redo if for me from then

---

### Post by Paqman on 2008-04-25
> **jdw1584 said:**
> should i just turn the free space into a partition or what?

You could. Or you could expand the partitions you already have to include that space.

Shrinking or expanding partitions can be very slow though. Don't do it if you'll need the computer in the next couple of hours.

---

### Post by ssican on 2008-04-25
This TUTORIAL will help: "RESIZING A WINDOWS PARTITION":
[http://www.easy-ubuntu-linux.com/resize-windows-partition.html](http://www.easy-ubuntu-linux.com/resize-windows-partition.html)

Creating the First Partition For Ubuntu Linux:
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html)

---

### Post by ssican on 2008-04-25
IF the second partition is just 13 MB (NOT 13GB), make the install of the Ubuntu in the FREE SPACE of 150GB. 13MB is a space very little.

---

