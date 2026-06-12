---
title: "how to repair Windows Boot Manager on dual OS (Windows 7 / Ubuntu 12.04)?"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by Aeons Midgard on 2012-09-26
Hi all,

first of all i am new in Ubuntu and using Windows 7 as my default OS... and as a trial run before i format my pc i installed Ubuntu 12.04... after i checked it and both OS (Win7 / Ubuntu 12.04) is perfecty running on dual boot... afterwards i format my pc with freshly formatted hard disk without any partitions and Win7 as a default OS but when i restart my pc... my Windows Boot Manager displays Windows and Ubuntu but i have not yet installed my Ubuntu 12.04... and when i install Ubuntu 12.04 again and i restarted my pc... on my Windows Boot Manager it displays Windows, Ubuntu, Ubuntu... i just follow this instructions on how to install Ubuntu 12.04 on Windows: [http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

how can i remove the excess Ubuntu and fix my Windows Boot Manager???

-thanks...

below is a sample screen shot link of the problem that i have encountered...



[http://www.flickr.com/photos/87782156@N08/8028500607/in/photostream](http://www.flickr.com/photos/87782156@N08/8028500607/in/photostream)

---

### Post by critin on 2012-09-26
Have you seen if ubuntu boots up?  I would try both entries just to see if the os's are actually there.  Formatting would of course have deleted everything, but something remained.
Also in windows, take a look at the disk and see how it's partitioned.  I'm curious.

---

### Post by oldfred on 2012-09-26
Welcome to the forums.

It looks like you installed the wubi version of Ubuntu. That is for an extended test of Ubuntu without having to create separate partitions. It uses the Windows boot loader and is just a file with the full Ubuntu in that file (root.disk) in the Windows NTFS partition.

The entries you have are in the Windows BCD. You need to use Windows repair console and bcdEdit to edit the BCD. Do both entries boot wubi? You can only have one install of wubi or one root.disk file. So if both entries work it probably is just booting the same install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)
[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.

---

### Post by Aeons Midgard on 2012-09-27
> **critin said:**
> Have you seen if ubuntu boots up?  I would try both entries just to see if the os's are actually there.  Formatting would of course have deleted everything, but something remained.
Also in windows, take a look at the disk and see how it's partitioned.  I'm curious.

actually i reformat my hard disk again but after i install Win7 again when i restart my pc the Windows Boot Manager shows up displaying Windows and Ubuntu as choices for which OS would i use... even thou my hard disk is freshly formatted but if i try to access Ubuntu... my Windows System Recovery shows up... i really just want to delete the extra Ubuntu choice in my Windows Boot Manager...

-thanks

---

### Post by critin on 2012-09-27
> **Aeons Midgard said:**
> actually i reformat my hard disk again but after i install Win7 again when i restart my pc the Windows Boot Manager shows up displaying Windows and Ubuntu as choices for which OS would i use... even thou my hard disk is freshly formatted but if i try to access Ubuntu... my Windows System Recovery shows up... i really just want to delete the extra Ubuntu choice in my Windows Boot Manager...

-thanks

Hi, Aeons,  

[[COLOR=#DD4814]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711")  whose post is just after mine,  states you've installed a Wubi version of ubuntu.   Is it installed inside windows?  You will want to follow any suggestions offered from oldfred.  They are reliable.

I just want to ask a couple of questions.
After you formatted the 'whole' disk, did you reinstall windows from an original, official dvd or from a cloned hard disk copied after you installed ubuntu?   Ubuntu will not be on the windows disk and formatting will take it off the hard disk, so it would be impossible for it to be there unless you used a recent cloned copy of the hard disk.  

If you used Wubi, the windows ubuntu installer, go into the Add/Remove programs through the Control Panel and find Ubuntu or Wubi, and just uninstall it.
> 
 i reformat my hard disk again but after i install Win7 againAnd you did NOT install ubuntu again after this?

---

### Post by Aeons Midgard on 2012-09-27
> **critin said:**
> Hi, Aeons, 

oldfred whose post is just after mine, believes you've installed a Wubi version of ubuntu, did you? Is it installed inside windows? I would follow any suggestions offered from oldfred.

After you formatted the 'whole' disk, did you reinstall windows from a dvd or from a cloned disk? Ubuntu will not be on the windows disk and formatting will take it off the hard disk, so it would be impossible for it to be there unless you used a cloned copy of the hard disk. 

If you used Wubi, the windows ubuntu installer, go into the Add/Remove programs through the Control Panel and find Ubuntu or Wubi, and just uninstall it.

And you did NOT install ubuntu again after this?

> After you formatted the 'whole' disk, did you reinstall windows from a dvd or from a cloned disk?
i did reinstall windows from dvd...

actually im new in Ubuntu and currently at work and ill try **oldfred** advice when i got home...

-thanks:D

---

### Post by oldfred on 2012-09-27
A total reinstall would remove all traces of wubi, which can be a problem if you had data in wubi. And it should create a totally new BCD that would not have any Ubuntu entries in the BCD. 
So very strange. Or we may need more information to know what has happened.

---

### Post by darkomano on 2012-09-27
For viewing/editing of complete BCD contents you can use [Visual BCD Editor]("http://www.boyans.net") 
(runs on Vista, Windows 7 / Windows 8 ).
 
Select the first loader for Ubuntu (click on loader in left pane).
In right pane you can see drive and path to file on disk which is starting the load (first stage of Ubuntu boot - a mbr file).
Check if file exists.
If file exists then this is a valid loader entry else you can delete the loader with
right-click and select "Delete loader/object".
 
Do the same for the second loader.
 
If a **loader is really valid** you have to try **if it really can boot the destination OS**.

---

