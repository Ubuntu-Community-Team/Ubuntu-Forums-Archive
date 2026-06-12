---
title: "Partition sizes for 5 users?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by speeddad on 2008-05-19
I am getting a new computer and I want to install kubuntu 8.04 on it tonight.  What how big should the partitions (home, users, swap) be for 5 users?  

The computer has 2gigs of ram.  It will be dual boot with XP.  It has a blank 500gb hdd. It is a home computer, mainly used to surf, write papers, listen to music, watch video (TV card), and play a few games for the kids (emulators). 

Thanks for the help.

---

### Post by django0909 on 2008-05-19
If you only have one operating system, you don't need to partition the drive up. Just install kubuntu and create 5 user accounts.

And then, if you want to limit the amount of the drive each account gets, you can do this when you set the accounts up as far as I know.

---

### Post by kellemes on 2008-05-19
> **speeddad said:**
> I am getting a new computer and I want to install kubuntu 8.04 on it tonight.  What how big should the partitions (home, users, swap) be for 5 users?  

The computer has 2gigs of ram.  It will be dual boot with XP.  It has a blank 500gb hdd. It is a home computer, mainly used to surf, write papers, listen to music, watch video (TV card), and play a few games for the kids (emulators). 

Thanks for the help.

Swap-partition should be 2 times the amount of ram, with a max of 2Gb.
So make it 2Gb and you're fine.
Root-partition shouldn't have to be more then 10Gb.
Home-partition is basically where most stuff will be stored, especially when downloading from the internet, storing multimedia etc.. Kids often have a habit of downloading the hole internet on there drive ;-)
Personally my home is using 8Gb out of 12, nothing spectacular in it. Currently 1 or 2 iso's of GNU/Linux distro's. I keep my multimedia (music/movies) on a separate drive.
You can make your home-partition as large as you please, or you can create an extra partition for storing multimedia, backup stuff or use it to share files between the users.. whatever..

---

