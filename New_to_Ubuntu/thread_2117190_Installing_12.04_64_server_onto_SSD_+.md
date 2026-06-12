---
title: "Installing 12.04_64 server onto SSD +"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by paarono on 2013-02-17
Hello, I have embarked on building a new home server to function as a part time NFS, part time media center and also to play around with some virtulaization.  I started this project out following this guide and it has been an eye opener for me - [http://www.havetheknowhow.com](http://www.havetheknowhow.com)

I opted to get a 128GB SSD for the OS and "front end" and a raid5 set up for the bulk of my media files and home sharing. 

Question is how should I best utilize the SSD and RAID together? I glossed over some other threads talking about where to put the swap file to get the most speed out of the SSD with out overworking the SSD. This is when i realized I may not be thinking of the ideal set up.

I am doing this all as a learning exercise so any pointers or things to consider would be much appreciated!

---

### Post by paarono on 2013-03-14
For any one else looking into this i came across this guide - [http://wiki.debian.org/Multi%20HDD/SSD%20Partition%20Scheme](http://wiki.debian.org/Multi%20HDD/SSD%20Partition%20Scheme)

---

### Post by Paqman on 2013-03-14
> **paarono said:**
> 
Question is how should I best utilize the SSD and RAID together? I glossed over some other threads talking about where to put the swap file to get the most speed out of the SSD with out overworking the SSD. This is when i realized I may not be thinking of the ideal set up.


I would put the whole OS on the SSD, with the actual storage on the big array (so create some mount points like (/mnt/stuff and specify that to be mounted on the array). As for swap, how crucial it is to you depends on how much RAM you have and what workloads you expect. For a file server you're probably not going to be using a lot of RAM, so you might find you have little need for swap. If this was the case I would [reduce the swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") right down and use a swap file instead of a partition. This would allow any swap usage you did have to be simple managed by the SSD's normal wear leveling algorithms.
Swap is used when RAM starts to run low, so if you're going to be running anything that can munch a lot of RAM (web server, game server, etc) then you'll probably want a decent sized swap, otherwise a pretty minimal one will suffice. My desktop only runs a 512MB swap file, for example.

Some other optimisations you'll want to include:
[LIST=1]
[*]Add the options "discard" to any lines in /etc/fstab that mount partitions on the SSD. This enables the ATA TRIM command, which is good for drive performance over time.
[*]Consider also adding the option "noatime" instead of the default "relatime", also on /etc/fstab.
[*]As mentioned in that guide some parts of the system that contain non-critical data can be mounted on ramdisks, such as /tmp. I wouldn't mount /var there like that guide suggests, or you'll lose your logs when the system shuts down. Unless you're backing up your logs somewhere that's a bad idea.
[/LIST]

Some people also mess about with the disk scheduler and use alternative filesystems, but I'm not convinced and of that is necessary.

---

