---
title: "Advice on backup methods, schedules, applications, for my situation"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by anachronism2 on 2013-09-23
I am a new Ubuntu 12.04 Precise user with little knowledge of the command line. I need to maintain a full system backup in case of hard drive corruption, data corruption, or theft of laptop. I would currently prefer to use a GUI tool to ensure that my data is backed up, and then I would like to learn how to use rsync after I have the entire system backed up. Based on this and my current situation, I have decided on the following:

I have downloaded fwbackup, Grsync, and luckyBackup. The tools for fwbackup are beyond my current understanding. The other two programs provide me with a practical, efficient solution to backup my data cleanly, and luckyBackup includes features to allow for a gradual transition to full command line control. If a better choice for application exists for me, I am open to suggestions. Please include a brief statement of reason.

I would prefer to keep my backup on an encrypted SD card. I do not know what size is appropriate. I have a 16 GB one and, if possible, I would like to backup my entire system, including all of my updates and files. Do I need a larger size?

I do not have any understanding of the best schedule of backups for my situation, though I would like to learn about what I need. My computer use is not critical. Theft is the highest possiblity. I need to keep the critical programs needed for restoration as well as my files, and I would like to maintain my programs as they are updated.

This is my current situation: I am using my laptop just for personal use, primarily for web browsing and text files (programming scripts). I have slow broadband internet with a data cap, and it would be more practical if I could avoid downloading updates if I have to restore my data. In the event that my laptop is stolen, I will need to be able to install Ubuntu on another computer (I have one live CD, and I intend to burn a new one from my current system once I have all of the updates) and restore my system state and files. Therefore, I need a method and application that is flexible across different computer architectures (i.e., an application that offers guidance for which files and programs cannot be installed on my new computer and which ones need a new library). I am very busy with multiple jobs, and I return home for a short time only in the evening, so I would prefer to have the comfort of being able to carry my backup on an SD card in my pocket. 

For application advice, links to the Launchpad would be appreciated, or the tarball if it is not part of the repository. For methods or scheduling advice, a brief explanation would be appreciated. 

P.S. Because of my work schedule, I will not be able to reply to this thread until 1:30PM central time tommorrow.

Thanks!

---

### Post by Pako Pako on 2013-09-24
Would you be open to [imaging the entirety of your drive](https://help.ubuntu.com/community/DriveImaging)?

"Making an image" of a partition is like "clone everything down to the last detail," so that upon restoration, absolutely everything goes back to the way it was. The drawback of this is the sheer size "absolutely everything" takes up.

My HDD is only 32GB in size, broken up into 8GB chunks. Let's call them C, D, E, F; C being the most important (programs) and F being the least (games). I could image the entire drive, but it would take 32GB of space. Or I could image just the C-chunk (8 GB), as long as I restored it (along with the MBR) to a similar or larger drive.

---

### Post by slickymaster on 2013-09-24
There's [Remastersys]("http://www.geekconnection.org/remastersys"). You can use it for a full system backup onto an installable CD, DVD or USB drive - this will also include your personal data and you can later use it like any live CD/USB to reinstall your whole system and data.

---

### Post by mastablasta on 2013-09-24
might be better to do a system image while at home and on the go backup only data with rsync or grsync. grsync is only a GUI tool for command line program.

---

### Post by Jonathan Precise on 2013-09-24
Try Clonezilla (Google-it)

---

### Post by anachronism2 on 2013-09-24
> **Jonathan Precise said:**
> Try Clonezilla (Google-it)

Thank you, I was unaware of Clonezilla. I am very intrigued by the concept, a small Linux distro for backups and it even makes a recovery disk. I have one reservation: For maintaining system-critical files, how many times should be the maximum for burning a DVD+RW disc? Searching this forum and Google offers a wide range of answers. If I can't be certain, I can at least strike a balance. I could reburn the DVD RW backup twice a month and keep weekly backups of the system on a SD card, as well as maintain a recovery disk. As long as I make sure to keep plenty of notes for scheduling that.

---

### Post by whitesmith on 2013-09-24
I use Clonezilla to create weekly images of my boot partition and Simple Backup for hourly incremental backups of $HOME.

---

### Post by Cyril380 on 2013-09-24
Clonezilla is temperamental, the one inside Parted Magic is easier to use.Be sure the /home is small otherwise the size of the backup will discourage you to do frequent clones. I use symlinks to keep my system size to a minimum (5G - no separate /home partition).

---

### Post by mastablasta on 2013-09-25
and for parted redo backup has a good interface,

well you said yoru problem is that you want to keep backup in case someone stole the laptop that you don't need to redownload the os+all updates due to limited bandwidth. in that case it would be really go enough to create an image once a week after you do the updates. i would clone it to external drive instead of to DVD.

---

