---
title: "Building a new system"
date: 2016-07-23
forum: New to Ubuntu
---

### Post by jon114 on 2016-07-23
Fairly new to Ubuntu Linux and wanting to ask some advice.
I've installed 14.04 & 16.04 on a couple of of laptops but that is there limit of my knowledge so far but my next project will be a bit more involved.
A windows desktop that I was using as a media streamer & photo backup device has just died with disk failure so I am considering rebuilding it as a sort of home office server/media streamer.
My thoughts are to install 3 new drives, 1 fairly small for the OS and a pair of 1TB drives for the files.
I was thinking 1 drive for music & 1 for photos with office type files on the smaller OS drive or do I do all streaming from 1 drive and set the other up as a back up, RAID or similar?
So my questions are how straight forward will this be for a noob and is my plan the right way of going about it?
Any and all helpful comments very welcome.
Jon

---

### Post by TheFu on 2016-07-23
Don't touch RAID. RAID is for HA and nothing else. Plus you still need backups with RAID. RAID solves only 2 problems, high availability and possibly added performance (if a $300 RAID card is used). It introduces lots and lots of complexity that aren't usually needed in a home environment.

DO setup backups. Backups solve 1000 problems. Make certain they are versioned, not just mirrors/copies, at least for the OS, settings, etc. It isn't much effort to keep 60 days of versioned backups.

Do you have the software to be used planned out for the streaming media and photos or would options for that be appreciated?

---

### Post by jon114 on 2016-07-23
Thanks Fu, so raid not the way to go then. What would you recommend for backup, built in option (deja-dup) seems easy to use, does it compress the resulting file?
Media streaming I have always used Subsonic, easy to install and setup and plenty of client device options. Keeps everything in one place music, photo's & videos.

---

### Post by TheFu on 2016-07-23
Don't know much about deja-dup or duplicity. Tried them years ago and didn't like the outcome (tons of tiny files, needing a  non-standard tool to restore, old-style backups with weekly full and daily incremental). Search these forums for issues with corruption on whatever backup tool you use, so they can be avoided.  Also, be certain to test the restore. After all, THAT is the entire point of backups.  
 
You should use whatever backup tool works for your needs.  I use **rdiff-backup** because it doesn't have a GUI, the last backup version is a mirror, and prior versions are diffs from that mirror. 60 days of daily backups requires about 1.20x the storage of the original files. Encryption isn't built-into rdiff-backup, but that is easy to add with other tools. I run servers and need a backup tool that works without a GUI required. Have a basic 100 line backup script that is modified slightly for each system depending on what it does, what is installed, and what needs to be backed up (DBs, websites, blogs, email, desktop stuff, etc.). You get the idea.

Never used subsonic, but there seem to be lots of people who like it and a few forks so it won't die.  Been using Plex here for a few years and Kodi/xbmc before that and simple network shares prior to that. Like most things about it, except it isn't F/LOSS, but it is free. It centralizes storage, supports playback on lots and lots of devices, with transcoding as needed for each device.  For remote access, I just use a VPN connection - no need to pay them for anything or even have a Plex online account.

Sounds like you have a plan that can be executed. Good luck!

---

### Post by smelheim85 on 2016-07-23
jon114,

Look up a command line tool called rsync.  It's an old backup utility that still works well.  Although I don't have multiple servers to back up I know several people that still use it.  It's installed on most *nix systems and well documented.  As for RAID, I have never used it before and can't give much of an insight light TheFu gave.  There are several backup utilities out there and you will want to find the one that works before for what you are doing.

---

### Post by jon114 on 2016-07-23
Thanks to both, I'll do some research on backup apps and see what looks right for me and do a bit of testing.
What about the disk organisation? Is a dedicated disk per media type over the top or would I be better keeping all media together and dedicating 1 disk for backup? Actually typing that I think yes,  an OS disk, a streaming disk and a backup disk sounds like the most sense?

---

### Post by smelheim85 on 2016-07-23
This is more preferences.  I know some will have the same disk for data and the / directory on a separate disk.  Sometimes people want to just have one disk for creating multiple partitions.  Since you have multiple disks I would suggest one for the OS and one for your data, if you have one more then you that for backup.  The reason for multiple disk really is for performance and redundancy.  So the small disk is ideal for the OS because it won't need all that much your music though should have the bulk of disk space and it's always a good idea to have a back in-case of disk failure.  But as always this is my preference others will think of different setups but it boils down to what's best for you and you level of experience connecting the disks to talk to each other.

---

### Post by Bucky Ball on 2016-07-23
I would go SSD for the OS (you only need a small one as you will be keeping your personal data on HDDs) and a couple of HDDs for data, if you need that many. You might get away with one 2Gb or 4Gb HDD.

That way, OS is speedy and you only need 20Gb (I generally use 15Gb) to install the OS. You then have room to dual, triple, quadruple boot, whatever, from the SSD. I have 14.04, 16.04, Win7 and two virtual machine partitions currently on my SSD with 40Gb to spare. It is a 128Gb SSD. All personal data (and /swap) on HDD.

---

### Post by SuperFreak on 2016-07-23
2 GB HD  Hmm

---

### Post by jon114 on 2016-07-24
I think he probably meant to type 2TB HDD.
Thanks for all the comments and think I'm happy with the way to go forward.
Is there such a thing as an ideal compatible HDD spec for Ubuntu? Was going to buy WD caviar blue as they seem decent spec at good price but read a couple of bad reviews.
The drive that just failed was Seagate Barracuda but may have a look at those also.
Any particular favourites and yes will be going for SSD for the main system drive.

---

### Post by jon114 on 2016-07-24
OK so why can I buy a 2.5" SSD for £40 and a cradle for a fiver but the same drive in 3.5" is £340? That's annoying

---

### Post by oldfred on 2016-07-24
I recently built a new SFF system. 
I ordered an SSD & HDD. Was going to get a 3.5" standard drive but pc part picker pointed out that my case only supported 2.5" drives.
And motherboard supported M.2 drive, so I ordered that.
When I saw drive cartons the M.2 drive carton was almost as large as 2.5" HDD, and I did not think much about it. But when I opened box a tiny flash drive size drive fell out. Easy to install and has worked well to date.

       oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

---

### Post by Bucky Ball on 2016-07-24
I only ever use WD HDDs. Blue are fine. What are you using the drive for? That would dictate the colour that is best for you. If you want some power saving and don't need 7200rpm speeds constantly, go for the WD Green. That is all I use for backups and stuff. Have done for years.

---

### Post by jon114 on 2016-07-24
Have ordered a Sandisk ssd as the main drive for the OS and a pair of WD 1TB HDD for music, picture and video streaming. Even found time to go through the hardware comcompatibility thread and check my video card is good to go so fingers crossed it should all play happily together.
Thanks for the advice folks &#55357;&#56832;

---

### Post by Bucky Ball on 2016-07-24
Good news and good luck.

You might like to mark this thread as solved if you're happy and update us with how you go. Marking as solved won't close the thread to further discussion but it will help others. :)

Don't hesitate to post a new thread is you have issues/questions with anything else (installing, putting the pieces together, etc.).

---

### Post by jon114 on 2016-07-25
Thanks Bucky, will do as soon as I get to a PC.
If I get chance I'll try to jot everything down as I go along and see if I can knock it together into a post along the lines of "if I can do it anyone can".

---

### Post by Bucky Ball on 2016-07-25
> **jon114 said:**
> If I get chance I'll try to jot everything down as I go along and see if I can knock it together into a post along the lines of "if I can do it anyone can".

Good plan and good luck. ;)

---

### Post by Tadaen_Sylvermane on 2016-07-25
I hope I'm not to late. I suggest if using multiple spinning drives use LVM instead of static partitions. Then you don't end up with one drive having tons of space, the other running out. Also easy to add to the pool if need to.

---

### Post by jon114 on 2016-07-26
Hi Tadaen, not seen LVM but no not had time to do anything yet.
Had a quick read and my first thought was yes OK looks flexible and a good idea for future mods, then I read the "How to get started with LVM" section and needed a little sit down. Think I'm going to have enough to do keeping things straight as it is but thanks for the suggestion.

---

