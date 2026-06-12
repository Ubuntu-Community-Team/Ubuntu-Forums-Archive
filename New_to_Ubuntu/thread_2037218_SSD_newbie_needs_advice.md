---
title: "SSD newbie needs advice"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by acevb on 2012-08-03
I purchased an SSD and have it successfully installed and working in my machine with Ubuntu 12.04 as the OS. My old set up was with a 2.0 TB hard drive that is in perfect condition and I have backed up all the documents pictures and what not onto an external hard drive. My question is, what do I need to do to have a set up that will allow me to use the SSD for the operating system and programs/applications and the hard drive for storing documents, pictures and things of that nature?
Any program that I would like to put onto the new SSD I have the disks for them so re-installation will not be an issue. My master plan is to have Windows 7 running in Virtualbox with some windows specific stuff like Office 2010. While Ubuntu 12.04 is the main OS. If anyone can point me to documentation that would assist me in my project or has any advise for me I would greatly appreciate the help.

---

### Post by oldfred on 2012-08-03
Welcome to the forums.

If you have Ubuntu installed to the SSD, you just need to mount the data partition(s) from the hard drive to use them for data. I do that as my standard now. I have /home still on my SSD, but it only has the hidden files & folders that are user configuration. Even some hidden folders are moved as they have a lot of data like Firefox & Thunderbird profiles.

I have my data separate as I multi-boot and want data but not any settings from /home in every install.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

