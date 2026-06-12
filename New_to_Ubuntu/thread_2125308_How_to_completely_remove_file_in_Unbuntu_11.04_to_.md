---
title: "How to completely remove file in Unbuntu 11.04 to reclaim HDD space"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by fishman35 on 2013-03-13
Hello alll. I use my Ubuntu box with Clonezilla and use it to image systems. Over time my hard drive fills up. I go to delete old images, but never get the space back. There is only "send to trash", no delete when right clicking. 

One thing I have noticed is that when choosing "send to trash", the trash can never recieves it, and even after running the command to empty the trash, the hard drive space is not given back. It appears that Bleachbit goes after temp files, cookies, dead links, etc. But these are GB files I am removing, and the space never comes back. If I continue to add, the hard drive will become full, then the dreaded "low resolution mode" happens when the disk space becomes too full. This one is a freakin nightmare!!!

Is there a way to just permenantly delete the file without having to dance around in the terminal trying to find what directories have large files or what is "in use" still, etc? I hate to say it, but deleting files in Windows is right-click, delete, empty recycle bin, space back again. 



Surely there must be a way? Thanks!

---

### Post by ibjsb4 on 2013-03-13
Yep, in Nautilus

[ATTACH=CONFIG]240138[/ATTACH]

---

### Post by sudodus on 2013-03-13
> **fishman35 said:**
> Hello alll. I use my Ubuntu box with Clonezilla and use it to image systems. Over time my hard drive fills up. I go to delete old images, but never get the space back. There is only "send to trash", no delete when right clicking. 

One thing I have noticed is that when choosing "send to trash", the trash can never recieves it, and even after running the command to empty the trash, the hard drive space is not given back. It appears that Bleachbit goes after temp files, cookies, dead links, etc. But these are GB files I am removing, and the space never comes back. If I continue to add, the hard drive will become full, then the dreaded "low resolution mode" happens when the disk space becomes too full. This one is a freakin nightmare!!!

Either something is wrong with your system, or you do not understand what is happening.

***Running the file browser***: If you send a file to trash, it is simply moved (to the .trash directory on the particular partition or the trash subdirectory in your home partition). But when you delete it from the trashcan, there should be more free space. If the file is too big it might be wiped directly, and you would be notified about that.

***Running terminal window commands***: if you use the command ***rm*** for example ```
rm testfile.txt
``` that file will be wiped directly. It will *not* go to any trashcan. This may be convenient, but is more risky. See ```
man rm
```
> 
Is there a way to just permenantly delete the file without having to dance around in the terminal trying to find what directories have large files or what is "in use" still, etc? I hate to say it, but deleting files in Windows is right-click, delete, empty recycle bin, space back again. 

Surely there must be a way? Thanks!

There are ways both in the file browser and in the terminal window. For me, it is not more difficult than in Windows, actually you should have very similar behaviour in the file browser, and as shown by *        ibjsb4* you can add direct removal to the right-click menu.

+ In addition to this I would suggest that you use ***baobab*** to get an overview of your file system to identify big files and big directories. ```
sudo apt-get install baobab
```

+ And I would suggest that you use ***Ubuntu Tweak*** to clean you system files. See this link, use 'tualatrix'

[[COLOR=#ff0000]http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html[/COLOR]]("http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html")

---

### Post by scratman on 2013-03-13
Shift + Delete key will remove a file and bypass the Recycle Bin.  baobab (also referred to as Disk Usage Analyser) can be used to locate the largest folders/files on your system, which can be useful for freeing up space that is not required.  Additionally, DupeGuru can inform you of duplicated files on your machine, which can rapidly free up space.

---

### Post by sudodus on 2013-03-14
I just had another look at the title of your thread.

> Re: How to completely remove file in Unbuntu [COLOR=#ff0000]11.04[/COLOR] to reclaim HDD space

This version of Ubuntu has passed end of life, and will receive no more security updates. And you will have problems installing new software too, because the repositories are not active.

So I recommend that you backup your personal files and/or make a /home partition and install a current version of Ubuntu. If your computer is getting old, it is a good idea to test not only standard Ubuntu, but also the light-weight Xubuntu and the ultra-light-weight Lubuntu flavours. The current versions are 12.04 LTS and 12.10. Ubuntu and Xubuntu (but not Lubuntu) have LTS, long time support.

---

### Post by fishman35 on 2013-03-24
Thanks everyone. The simple setting under preferrences while in Nautilus took care of it.

---

