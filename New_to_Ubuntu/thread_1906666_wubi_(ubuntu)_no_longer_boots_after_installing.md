---
title: "wubi (ubuntu) no longer boots after installing"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by robertkingnz on 2012-01-09
Hi, I'm reasonably experienced with computers but not with sys admin type stuff.

As you can see from the attached jpg, I installed ubuntu using wubi. It worked fine (so i could dual boot into either vista or ubuntu).

**When I installed MinGW on vista, Ubuntu stopped working (I couldn't boot into ubuntu anymore).**

If you don't know what MinGW is, this is the blog post that I was following which has a link to MinGW:
[http://blog.eddsn.com/2010/05/unable-to-find-vcvarsall-bat/](http://blog.eddsn.com/2010/05/unable-to-find-vcvarsall-bat/)


What happens when I turn on my computer:
I get the usual screen asking If i want to boot into windows or vista. If I select the default of ubuntu, I get an error:

[B]Try (hd0,0): NTFS5: error: "prefix" is not set.
error: no such device: /ubuntu/disks/root.disk.
error: no such device: /ubuntu/install/boot/grub/grub.cfg[/B]

Then it goes into a "Minimal BASH-like" terminal where i can type a few commands such as reboot


It may be worth noting that at one stage, from within windows, I set windows as my default boot using BCDedit and it was working fine. Then when I installed MinGW it made ubuntu my default boot.

I also uploaded a picture of disk management in case that helps.


If I cant find root.disk does that mean I've lost all my work?
I Could reinstall if need be but I would like to try to recover a file if possible..

Thanks.. Please let me know if you need anything else

---

### Post by Frogs Hair on 2012-01-09
Hello and Welcome 

This is a big thread , but I know this has happened and been resolved before .
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (Wubi Mega) 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by robertkingnz on 2012-01-09
I'm stuck on this bit:
[http://ubuntuforums.org/showpost.php?p=10264157&postcount=33](http://ubuntuforums.org/showpost.php?p=10264157&postcount=33)
I don't know what to put for  (X,Y and sda1)

---

### Post by robertkingnz on 2012-01-09
> **robertkingnz said:**
> I'm stuck on this bit:
[http://ubuntuforums.org/showpost.php?p=10264157&postcount=33](http://ubuntuforums.org/showpost.php?p=10264157&postcount=33)
I don't know what to put for  (X,Y and sda1)

Here is what I tried:

grub> insmod ntfs
grub> set root=(hd0,0)
grub> loopback (loop0) /ubuntu/disks/root.disk
error: no such partition.
grub> set root=(hd0,1)
grub> loopback (loop0) /ubuntu/disks/root.disk
error: file not found.
grub> set root=(hd0,2)
grub> loopback (loop0) /ubuntu/disks/root.disk
error: file not found.


I guess I'll give up on this, and try solution1 using a LiveUSB to boot into ubuntu. fingers crossed, ill let you know if it works.

---

### Post by bcbc on 2012-01-09
Problem 1 and 2, and therefore the solutions don't apply anymore. Can you confirm whether you still have your root.disk? (In \ubuntu\disks\ directory)?

If not, refer to this: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

PS to get to the found.000 directory you need an administrator command prompt.

---

### Post by robertkingnz on 2012-01-09
> Microsoft Windows [Version 6.0.6000]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\Robert>cd C:\ubuntu

C:\ubuntu>dir
 Volume in drive C has no label.
 Volume Serial Number is E424-435E

 Directory of C:\ubuntu

07/05/2011  12:24 p.m.    <DIR>          .
07/05/2011  12:24 p.m.    <DIR>          ..
08/05/2011  02:33 a.m.    <DIR>          install
07/05/2011  12:24 p.m.             1,150 Ubuntu.ico
07/05/2011  12:24 p.m.         1,530,520 uninstall-wubi.exe
07/05/2011  12:24 p.m.    <DIR>          winboot
               2 File(s)      1,531,670 bytes
               4 Dir(s)  142,406,430,720 bytes free

C:\ubuntu>

^ from above, I can't find the disks folder.

Also I think i did have the latest ubuntu installed so that mega thread probably wont work for me.

bcbc, I'm following the guide on your blog post, it looks promising. I'm just rebooting for step one now, thanks.

---

### Post by robertkingnz on 2012-01-09
Alas, I haven't found anything:

> Microsoft Windows [Version 6.0.6000]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Windows\system32>cd C:\found.000

C:\found.000>dir
 Volume in drive C has no label.
 Volume Serial Number is E424-435E

 Directory of C:\found.000

17/11/2011  07:06 a.m.    <DIR>          dir0000.chk
               0 File(s)              0 bytes
               1 Dir(s)  142,409,752,576 bytes free

C:\found.000>


I'm guessing there isn't anything I can do then..


From the comments in your blog you say:
> 
bcbc said...
If you cannot find the root.disk, then your Ubuntu install (and everything on it) is gone.

Jitesh, the Try (hd0,0) and the "prefix not set" error are benign messages that happen on all installs. If it's not booting then the problem is likely the root.disk. Run chkdsk, confirm the root.disk is there, and try again.
December 21, 2011 4:19 PM


Alas, I'll have to reinstall. I'm guessing i'll have problems installing wubi, will it say "you must first uninstall ubuntu"? Do I just uninstall ubunutu using windows add and remove programs? How do i get the 10GB i gave to ubuntu back.

Should I mark this thread as "solved"

---

### Post by bcbc on 2012-01-09
The dir0000.chk folder is probably the \ubuntu\disks folder and within it you'll hopefully find the root.disk and swap.disk. (If it does then you can find the commands to copy it on that blog post).
> If the entire \ubuntu\disks folder is missing, you'll likely find a dir0000.chk directory and within that the root.disk, swap.disk and empty \boot\grub folders. Copy this back to \ubuntu renaming the directory to disks.

*C:\found.000>move dir0000.chk \ubuntu\disks*

---

### Post by robertkingnz on 2012-01-09
omg...  I just uninstalled ubuntu, I totally didn't even see that dir0000.chk was there!!

Is it possible for me to reinstall ubuntu and replace the disk?
I also have wubildr backed up..

Here is what was in the chk:
> 
C:\found.000>cd dir0000.chk

C:\found.000\dir0000.chk>dir
 Volume in drive C has no label.
 Volume Serial Number is E424-435E

 Directory of C:\found.000\dir0000.chk

17/11/2011  07:06 a.m.    <DIR>          .
17/11/2011  07:06 a.m.    <DIR>          ..
07/05/2011  12:24 p.m.    <DIR>          boot
15/11/2011  05:29 p.m.    31,188,844,544 root.disk
08/05/2011  02:28 a.m.       268,435,456 swap.disk
               2 File(s) 31,457,280,000 bytes
               3 Dir(s)  143,129,980,928 bytes free

C:\found.000\dir0000.chk>

---

### Post by bcbc on 2012-01-09
> **robertkingnz said:**
> omg...  I just uninstalled ubuntu, I totally didn't even see that dir0000.chk was there!!

Is it possible for me to reinstall ubuntu and replace the disk?
I also have wubildr backed up..

Yes - provided the root.disk is there you can recover it. What do you want to do? Reinstall Wubi or do a dual boot and just copy data off the root.disk?

---

### Post by robertkingnz on 2012-01-09
which would you recommend given my circumstances? I was thinking wubi would be easier to install..

---

### Post by bcbc on 2012-01-10
You can reinstall Wubi with a small root.disk (5GB) and then copy the files from dir0000.chk over \ubuntu\disks. This works without tweaking as long as you reinstall to the same 'drive' (partition).

However, you should probably try and figure out what caused the corruption in the first place. If it's from doing hard shutdowns then just avoid that: instead you can  you can safely reboot by holding [Alt+SysRq and pressing R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot").
If you don't know the cause of the corruption, then it's possible it could happen again. In that case, you may want to consider a normal dual boot or check for hardware incompatibilities (any errors in /var/log/syslog) etc.

---

### Post by robertkingnz on 2012-01-10
Alright, i've installed ubuntu with wubi, i've moved the disks back, now i'm testing it out! fingers crossed my next post will be from my old ubuntu

---

### Post by robertkingnz on 2012-01-10
eureka for i have found it!!

Thanks so much!! it's all working now :)

virtual hug :P


4 hours of trying = worth while!

---

### Post by bcbc on 2012-01-10
Great news!

Don't forget to clean up the 30GB file sitting in your found.000 directory ;)

Also, if you decide to switch to a normal dual boot, you can [migrate your Wubi install]("http://ubuntuforums.org/showthread.php?t=1519354"). In the meantime, especially if you're not sure what caused the corruption, keep regular backups of any data on the root.disk.

Enjoy!

---

