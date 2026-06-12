---
title: "[SOLVED] External USB Hard Drives for Backups"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by the.scarecrow on 2008-10-31
Hi

I intend to buy an external hard drive to use for backups only from both winXP and Ubuntu 8.04 Hardy. I have done a lot of forum reading to find that a drive that works well for one person causes problems or doesn't work for another.

So I plan to buy a Maxtor hard drive either 500GB or 750GB. I am going to connect it using winXP FIRST to ensure that the drive configures itself for NTFS. SECOND I will start Ubuntu and hopefully the Maxtor will appear with the others as just another windows drive.

Is this the best way to go? your thought are welcome.

Thanks
the.scarecrow

---

### Post by Daveth on 2008-10-31
I use a Freecom external usb/firewire 160gb drive for backups, though only for linux (nothing else used anymore), and this works fine. Just automounts, and then I run sbackup and off it goes. I would be inclined to go for the fastest port you can get. I do recall on here someone got what they thought was a standard external hard drive but it came with some nasty windows code embedded which caused all sorts of horrors, so do check it out before you buy.

---

### Post by the.scarecrow on 2008-11-01
Anyone got some comments good or bad about Maxtor? I haven't bought it yet.

the.scarecrow

---

### Post by pwc on 2008-11-01
I bought SimpleTech's 500 GB simple drive at Circuit City, think I paid about $90 and use it on my ubuntu 8.04 system. It works just like any flash drive, plug it in and up pops a window. File transfer is simple drag and drop. The thing I like about it is very quite and only powers up when you connect with usb.

---

### Post by reg4c on 2008-11-01
I forgot the maker of my drive so if someone can tell me how to find that out I will tell that that maker works weel for both Window$ and Linux.

Cheers

---

### Post by richg on 2008-11-01
I have been using a Maxtor external 80gb hard drive for at least three years. Since USB 1.1 is slow I installed a PCI Firewire card. With USB 2.0 this will probably not be an issue.
I started this when I had a 98SE PC and a Linux PC. Never, ever had any issues with it. I made a directory for Windows files and a directory for Linux files. Used the drive right out of the box. Never saw a need for formatting or partitioning.
I gave away the 98 PC two years ago and only have a Linux PC now. Linux handles all the Windows files just fine. I power down the drive until needed.
I have stayed with the KISS principle.
Just in case, I periodically burn all my files to a DVD which is kept off site. Small price.
I scan the label on the drives I buy and keep the photo in my PC for future reference. I have six removable hard drives.
[IMG]http://i98.photobucket.com/albums/l267/richg1998/Misc/Harddriverack.jpg[/IMG]

I use Western Digital, Seagate and Maxtor drives.

Rich

---

### Post by the.scarecrow on 2008-11-01
OK, I went to Maplins this PM and they had a promotion running on the Seagate Free Agent Desk 1TB at 99.99GBP. During my research I had read plenty of good reports about Seagate, so I asked the staff if they knew if it works with winXP and Ubuntu.

One member of staff was very familiar with Ubuntu and knew that it will work OK, so I bought it. I first connected it to a winXP Dell laptop and it worked perfectly although I did not run any of the included software. Next I connected it to my eleven year old Dell Latitude running Xubuntu and again no problems browsing, saving or reading files.

When I wanted to disconnect it I chose the Eject Drive option and this comes up with an error. However, removing and re-connecting several times did not cause any actual visible problems.

So I am relieved that it works fine in windows and linux, its very quiet and comes with a 5year warranty. It should keep all our data safe for many years to come.

the.scarecrow

---

### Post by kansasnoob on 2008-11-01
Sounds OK to me!

I use several external drives for different types of storage.

NTFS is fine, to make access from Ubuntu easy and efficient I recommend installing pmount in Ubuntu (it's in the repos), and either ntfs-config or ntfsprogs (both in the repos).

I use ntfsprogs but it will allow you to destroy ntfs data! It's as safe as you are!

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by the.scarecrow on 2008-11-10
I have been using the Seagate Free Agent Desk 1TB for about 2 weeks now on Xubuntu 8.04, Ubuntu 8.04 an winXP SP2 with complete success.

When I first connected it to a PC I used winXP to check it out and moved all the pre-loaded software into a file for storage. I did not install any of the supplied apps. I just read the user manual. I also made sure it was ready for safe removal before shutting down winXP.

Then I used it on Xubuntu. It works perfectly except I get an error when I try to demount the drive. However, this has not in any way caused a problem in use.

Finally I have been using it on Ubuntu and it works perfectly I have not noticed any problems at all.

So I can recommend the Seagate Free Agent Desk 1TB.

the.scarecrow

---

