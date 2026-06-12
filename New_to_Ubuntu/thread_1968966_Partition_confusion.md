---
title: "Partition confusion"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by sonofbc on 2012-04-29
I am trying to install Ubuntu 12.04 and I re sized my hard drive and created a new partition. I also have an extra drive that I use for my important files. All my drives (partitions) have names but when I go to install Ubuntu from the DVD it does not tell me the names of the drives and further more it seems to be suggesting there are 7 different drives. It gives me things like sda1 and sda2 and sda5 and swap drive and funny things like that. I am afraid of screwing up my windows partition and or my special files that are stored on my spare drive. I also do not have any idea what the program is asking me or suggesting. How do I decipher this and why does Ubuntu not just show the names of the drives so that a normal person (as opposed to a geek) can understand what is going on?..

Any helpful hints would be welcome.

ps... I have tried to read a few installation sites but they are just as confusing with no real information on choosing the correct drive to install Ubuntu

---

### Post by strask on 2012-04-29
Ok it sounds like you created the new partition (the one you want to put ubuntu on) from windows. I think the easiest way for you to do this would be:

1) Go back into windows, find the partition that you want to put ubuntu on, and DELETE it. This will just leave a chunk of free space on your hard drive.
2) Then, in the ubuntu installer, tell it to use the free space for ubuntu.

The funny names you are seeing aren't really that hard to understand once you know the system... 
sda is the first disk. sdb is the second disk. sdc is the third disk, and so on.
sda1 is the first partition on the first disk. sdb4 is the fourth partition on the second hard disk, etc.

---

