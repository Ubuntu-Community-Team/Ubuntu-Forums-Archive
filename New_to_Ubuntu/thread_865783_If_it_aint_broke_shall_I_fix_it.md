---
title: "If it aint broke shall I fix it?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by dave.com on 2008-07-21
Hello all, recently I took on the project of installing Ubuntu on the 2nd Sata drive when I more or less stumbled onto the Ubuntu site in a Linux quest. That is to say I have 3 hard drives, 2 of them are sata, and a dvd-cdrom writable optical drive. I wished to keep my windows drive and I wished to install Ubuntu on its own drive, there was a free drive to play with like messing with online games so that became kinda a meeting ground between the 2 OS. 

For the curious, I used manual scheme and made a root partition, a boot partition 2nd and then a home partition using the reiserfs fs (first 2 partitions are ext3 fs), the swap partition is the only logical partition on that drive. The other sata is split in 2 partitions I labelled SATA-1A and SATA-1B (in case I ever need to know, inside XP), one is ntfs the other is fat32. I also used blkid's found Label to identify the XP hdd in Grub's menu.lst "other OS (section" title block (LABEL=<string>) under Rootnoverify=(hdx,x) and the map (hd0) (hd2), map (hd2) (hd0) makeactive, chainloader +1, boot lines. Lucky thing I had labelled my C:\> in WinXP before this setup (Dead C: lol).

This post is my success report, the grub bootloader launches both drives (XP kept its own mbr tho). But I do have some /etc/fstab auto-added entries that have marked the corresponding original device's file name at the commented line (identifying my device entries with a commented line so I know what teh hell I was doing.) 
Here is an simple illustration:
> # /dev/<string>   | UnKnow Device! |

The device details, its corresponding field entries, are all entered under that line. My computer is up and it is running, there's some tweaking ahead of me and some housecleaning, maybe some drivers to install and so on. So is this a concern? Should I ignore it, or is there a day down the road the autoset thinggy (something sure as hell wrote that stuff) is gunna spring a nasty suprise on my hardware settings. Might the entries I see in the fstab file not be the actual settings that are loaded in grub? Is something gunna conflict?

Feel free to pump me for info but I gotta warn ya's I read a lot of info, and I forget after a while. Plus, I am really quite new.

---

### Post by candtalan on 2008-07-21
Congratulations on your success, and Welcome!

The auto entries in fstab do not seem to be giving trouble, so you can ignore them if you want to. That does not stop you finding out more about fstab though does it?

It may be useful to keep a back up of fstab file (and maybe other files also of course), particularly if you begin to do experiments. 

It will be possible later to edit any file from the command line by using a live cd if you have to and if you know what to do. You also have a recovery mode that you can boot into initially if you wish, in an emergency.

You enjoy finding things out, so keep in mind that once you have used the password to get to root privilidges, there is nothing at all stopping you from hosing your system   :-) If that is a problem, go gently. Back up your stuff, and well done!

---

### Post by t0p on 2008-07-21
In reply to the question in the title of your thread "if it ain't broke shall I fix it?" I'd say:  Sure, why not?  And if you should inadvertently break it, then you can fix it all over again.  Or as some people put it: **"Ubuntu is yours to keep.  If you break it you can keep both halves!"** ;)

---

