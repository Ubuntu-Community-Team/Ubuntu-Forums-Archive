---
title: "Wrong disk capacity on fully-encrypted disk"
date: 2015-12-19
forum: New to Ubuntu
---

### Post by darris2 on 2015-12-19
I read through a bunch of threads on this topic, but none of them seem to address this particular issue. 
I'm using about 22G of space on a 250G HDD, but it says the HDD is full. 
When I use baobab, it tells me that I'm using 100% but it says my HDD is 21.7GB in size and all of the size is located in my ~/.Private folder that gets created when you encrypt the whole disk. 

Before I started deleting everything to make space (because I didn't know exactly what the error was), I was using about 100GB. So as I delete things, my disk "full" capacity goes down to whatever I have on it. 

I don't know what to do about this.

---

### Post by oldfred on 2015-12-19
Full disk encryption uses LVM which is a logical partition overlay over the physical partitions. It is an advanced partitioning system.
The physical partitions are always 100% full.
You have to use LVM tools to manage system.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[URL="http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html"]http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html

[/URL]
 14.04 Encrypt LVM install with dual boot Windows 8 UEFI/gpt- dusf
[http://ubuntuforums.org/showthread.php?t=2218477](http://ubuntuforums.org/showthread.php?t=2218477)
Older, now obsolete version, but shows details
13.10 LVM install - Herman
[URL="http://members.iinet.net.au/~herman546/index.html"]http://members.iinet.net.au/~herman546/index.html

[/URL]

[URL="http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html"]
[/URL]

---

