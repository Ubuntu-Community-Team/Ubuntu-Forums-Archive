---
title: "re-install ubuntu keeping your data and settings"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by Vedhas on 2014-06-12
Thanks for the detailed tutorial. I am a newbie btw. Would your method work in the post if my laptop hard disk got corrupted (?!) due to sudden power failure?

Details:
(1) My Acer laptop battery is dead, so I have been using my laptop directly using AC power through battery charger. Charger chord is little loose, so at one point in time, when using ubuntu system got switched off. This has happened many times before, so as usual, I tried turning it back on, but this time it would not be possible for me to get to ubuntu, I dont remember about windows i.e. whether or not grub was there. I 'think' I was able to get to windows, but not too sure.
(2) By booting through CD, I found that my windows data was safe, I backed it all up on external drive.
(3) As for my ubuntu data, I tried fsck with one tutorial online, but my bad: I answered 'Yes' to "....has deleted/unused inode. Clear?" for few times, until I got bit scared and aborted the fsck operation with ctrl+C. I believe at this point I lost some of my data (at least I lost it from the 'file' format, may be it was still there in 0's and 1's, I believe so because I managed to recover 'content' of many files in one huge txt file (explained in the next step) ??? )
(4) Using this tutorial: [http://myhowtosandprojects.blogspot.in/2009/04/recovering-data-from-disks-with-bad.html](http://myhowtosandprojects.blogspot.in/2009/04/recovering-data-from-disks-with-bad.html), I finally managed to access many of my ubuntu files successfully for the first time through CD boot. I backed up whatever I could see in my ubuntu drive to external harddrive. I had lost /root and many other directories, fortunately part of /home was still present,  this is where I found many of 'my' files, though many were lost. For some files, there were io errors probably because of ionode problem so those could not be backed up. Additionally, thanks to same tutorial above, I got content of all of the rest of the files into one huge text file. Please check the section "Method of Last Resort" in [http://myhowtosandprojects.blogspot.in/2009/04/recovering-data-from-disks-with-bad.html](http://myhowtosandprojects.blogspot.in/2009/04/recovering-data-from-disks-with-bad.html) and questions posted below from user "sahdeV" (me). There, basically, I need to know how do I now split this text file into different files like the originals.
(5) My question to you for this thread is, is it possible for me to reinstall ubuntu without losing data when only directories I have in ubuntu partition are lost+found, etc and home? I have backed up many files, but I am just hoping if there is anyway, I need not format (dreaded word for me) that drive -so that there remains a possibility to recovering my files. Currently, my installation is halting at "Saving installed packages page" like forever. I did not pay attention to last log in my previous attempts, but this time at least I am seeing last log to be 

June 12 15:32:22 ubuntu ubiquity[3207]: Step_before = stepMigrationAssistant 
Error opening file for reading: Permission denied

And after that hourly similar logs?
June 12 16:17:01 ubuntu CRON[10730]: (root) CMD (  cd / && run-parts --report /etc/cron.hourly)
June 12 17:17:01 ubuntu CRON[10746]: (root) CMD (  cd / && run-parts --report /etc/cron.hourly)
June 12 18:17:01 ubuntu CRON[10765]: (root) CMD (  cd / && run-parts --report /etc/cron.hourly)
June 12 19:17:01 ubuntu CRON[10785]: (root) CMD (  cd / && run-parts --report /etc/cron.hourly)

KINDLY HELP!!! :(

---

### Post by oldfred on 2014-06-13
Moved from the tutorial where posts are to be related to discussion of tutorial not request for help.
Tutorial on reinstall:
[http://ubuntuforums.org/showthread.php?t=2057342](http://ubuntuforums.org/showthread.php?t=2057342)

I still think you need to run fsck. And check hard drive status in Disks or Disk Utility. Continued crashes may cause damage to drive.

Second command auto answers the yes.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

"dirty"  reinstall overwrites all the Ubuntu files, but your data is not overwritten. But if not readable it will not fix it. So I think you need the fsck first.

---

