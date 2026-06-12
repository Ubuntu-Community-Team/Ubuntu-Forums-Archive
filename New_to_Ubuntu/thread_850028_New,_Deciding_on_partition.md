---
title: "New, Deciding on partition"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by madman587587 on 2008-07-05
OK, so I'm kinda new to this stuff, i have had heaps of experience with XP and networking but want to unleash from the shackles of Microsoft and head toward Linux.

This is where i have run into one problem, I know how to partion drives bla bla bla, but how should i do it?
I want to keep XP, so i will be doing a Dual-Boot with Windows and Ubuntu.


I have my primary HDD, 400GB SATA2 (with XP)
I also have a secondary HDD, 500GB SATA2

[IMG]http://www.psychocats.net/ubuntu/images/partitioning3.png[/IMG]

^that is what i think i should do, but i was wondering if Ubuntu supports / detects more then one HDD? and if i can make my secondary disk FAT32, so that it looks like this (with the secondary HDD been just FAT32)
[IMG]http://www.psychocats.net/ubuntu/images/partitioning2.png[/IMG]

Thanks for your help Guys and/or girls

---

### Post by bumanie on 2008-07-05
I would suggest you leave windows on the primary drive and install ubuntu to the secondary drive. There is longer any real need to have a shared FAT32 partition as ubuntu has read/write capability to ntfs (and it is well tested and stable). I have attached screen shots of my set up. As you can see no FAT32 and there is no problem reading/writing to ntfs once ntfs-3g and ntfsconfig are installed. I did a manual partition of ubuntu so as to have a separate /home partition.

Whoops they didn't come out right. I'll try again with a delay this time.

---

### Post by bumanie on 2008-07-05
Here is some clearer shots. Basically only have xp for my son who refuses to use ubuntu (too geekish he says). Have plenty of room to increase partition sizes if needed.

---

### Post by madman587587 on 2008-07-05
Now that's a good idea, but the problem is that both HDD are basically full, they have about 50GB - 60GB free on each, my secondary is just basically "My Movie Backups", so there is not alot of space and that is the only place i can put "My Movie Backups"

thanks

---

### Post by bumanie on 2008-07-05
Well, 50g is ample space for ubuntu 8g for / should be plenty (I made mine 20g to run virtualbox, which has now been symlinked elsewhere because it was getting too big) 1-2g for swap and the rest for /home, leaving 60g for for backups on the second drive. There are multiple ways to do things, none more right than another - comes down to personal preference, but I would encourage you do a manual partition, which is not hard. Grub works more easily if it has only one windows installation to deal with. Not sure whether your screenshots with xp on primary and secondary mean xp has been installed twice or whether you were describing the ntfs partition on the second drive as storage. As said FAT32 is not needed, that would be better made into ntfs seeing ubuntu reads/writes to ntfs. Other than that, you could set up how you have put in the screeshot. 
Primary could be xp with ubuntu / and swap at the end and you could make secondary as /home - ubuntu does not worry about having /home elsewhere. You could partition half as ntfs, half as ext3 - up to you, you know your setup and needs better than I do.
You will have to have a think and get back to the forum if you need help once you've decided which way to go. There are also many tutorials available on the internet, many with a slightly different focus on how to do things - have a read and then you can make better decisions.

---

### Post by madman587587 on 2008-07-05
Ok, so i was thinking of putting the Ubuntu Operating System on my primary HDD and my Home on my secondary, but where would i put the SWAP and is this posible

---

### Post by bumanie on 2008-07-05
As said above, do some pre-reading. I would choose manual with the radio button and partition from there or else from the live cd do in terminal (Applications --> Accessories --> Terminal) type > sudo apt-get install gparted --> enter and pre-partition with that it has a gui as per my screen shots. THe partition editor is under System --> Administration --> Partition editor. With 800g of hard drive it will take a couple of minutes to open up. 
Take note that linux names sata hdd as sd? so primary drive will be sda, secondary will be sdb and each partition will have a number, so the first partition on the first drive will be sda1, second partition on the first drive will be sda2 etc. To confuse things (but it's OK when you've had a bit of experience) grub names and counts differently, Primary hdd to grub is (hd0) and the first partition is denoted as 0 as grub starts its count at 0., thus the first partition on the first drive will be (hd0,0) to grub. 
As you have lots of backup movies etc. be careful and read first.

---

