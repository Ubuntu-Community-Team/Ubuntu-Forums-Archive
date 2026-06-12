---
title: "Ubuntu\Win7 dualboot, recovering MFT of a partition"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by chryssa1id on 2013-06-21
Hi, everyone. I have a problem with MFT of one of the partitions. I'll try to provide as many details as possible, I would be greateful for any help. Thanks in advance!

0. My setup
I have 2 hard drives
first one: 3 partitions - C:\ is where windows 7 is installed (~30Gb), D:\ (~100Gb) and E:\(~120Gb) are just there for the file storage.
second one: F:\ ubuntu (12.04) is installed here
I.e. [ C(win7) D(files) E(files) ] [ F(ubuntu) ]
I've been dualbooting it like this for a year now and everything worked perfectly with no problems.

1. Steps that followed to the problem
a. I wanted to install a program (matlab for my statistics course) and decided to use ubuntu for that. I installed everything just fine.
b. However, file "E:\matlab_install_dir\bin\matlab", which serves as the application startup, was opening only via gedit\notepad. 
c. I figured I had to check the "allow running file as a program" in the file properties. As soon as I checked it, it immediately unchecked itself.
d. I googled the problem and found out it could probably be caused by mounting the harddrives in "noexec" mode. (I've been mounting the harddrives D:\, E:\ with doubleclicking all this time and had no problems whatsoever).
e. I didn't want to change mount config files (was afraid to mess something up, the irony) so I googled and downloaded PySDM. 
f. I remounted E:\ as allowing me to execute binary files. Matlab worked as a charm.
g. I rebooted as win7. I wanted to delete some files from E:\ which I created while was in Ubuntu but, to my surprise, I couldn't (it said that I had no rights and there was some error, can't remember the exact words, unfortunately)
h. I went to "E:\" -> Properties - used the windows disk check tool. It started the check  and I went to grab a coffee when the lights went out (i live in a cheap flat with a lot of neigboors, this happens quite frequently when everyone decides they need a microwave and an iron turned on)
i. When it was fixed, I booted up win7 again and while booting up it said that my E:\ drive should be checked for consistency. Then it said that master file table was broken and when I logged in I couldn't acces my E:\ drive at all.
j. I googled some more and used the testdisk utility; it said that MFT could not be recovered.
k. Since I know that the drive is not physically damaged and I just messed it up 'logically' (either using PYSDM in ubuntu or when the windows check disk utility was interrupted in win7), can I repair it somehow?

Thanks!

---

### Post by chryssa1id on 2013-06-21
After I used the testdisk in ubuntu, my Win7 can't access D:\ either. What should I do? Will things like minitools partition wizard\etc. help me? Thanks again.
edit: I would appreciate even just an estimate of how many days I will need for recovering\finding the solution; I have to present my bachelor paper the next week and all the WolframMathematica projects and textbooks pdf are on the D:\ and E:\ drives.
edit: I fixed D:\ within Win7 with the minitool partition wizard (didn't evenhave to reboot,  the files just appeared again). Unfortunately, it couldn't fix E:\

---

### Post by Mark Phelps on 2013-06-21
The Minitool Partition Wizard has a couple of different options: (1) check the disk (runs CHKDSK), and (2) recovery the partition.

If you tried (1) on E:\ it didn't fix it, you should try (2) -- but if that works, it will overwrite the MFT with a saved version.  

However, I don't think the free version has (2).

An alternative is the EASUS Partition Master.  You can download it for free -- but I think you have to install it (in Windows).  However, I believe the free version also has the partition recovery option.

Another option, since you're having problems with a Windows filesystem partition, is to go to the Windows 7 forum (sevenforums.com) and ask there.

---

### Post by chryssa1id on 2013-06-21
Thanks for the reply! 

Yes, I used the 'check the filesystem' option in Minitool PW.

I also brought the HDD to the university since there is a lot of licensed software installed at my department. I used the R-Studio and after a scan it could see all the files on E:\ perfecty well, including extensions, hierarchy, size, etc. There are also some 'meta files' like 'MFT' and 'mirror MFT'. The problem is, the program doesn't allow to 'restore' with a simple click.

I used the boot-repair from Ubuntu and after that I don't see the E:\ in win7 anymore (it was visible though unaccessible before).

And yes, you are right - my question doesn't really relate to this forum, I know. Just the worst time for a student to get his filesystem messed up, so I didn't think clearly when I came here. Anyway, thanks again, I will try EASUS.

**edit: **So, most likely I'll just bring it back to the university tomorrow and recover all the files individually (since there is no option of recovering the partition in R-Studio, but you can copy the files, and so far it's the only program that sees all the files in there). After this, I'm going to just format the partition. Is this a good plan? Could there be a problem with copying the files from E:\ (via R-Studio) on the same hard drive, but different partition?

---

### Post by Mark Phelps on 2013-06-21
The general problem with trying to replicate a partition happens when there are hidden files, and other files whose location in the partition is critical -- but with a Data drive, you are unlikely to have either of these.

So, if you can read the drive well enough to copy off the files, have at it.

Did you try EASUS Partition Master? I believe it has the option to recover the partition -- which means it will copy the contents of the "mirror MFT" on top of the current "MFT".  IF this works, you will access restored to all the files easily.

---

### Post by chryssa1id on 2013-06-26
I didn't want to create another topic because the problem I'm having now is, apparently, caused by something I've done previously. It's not as important as losing all the data, but I would appreciate if anyone would explain to me what could cause it.

So, I've recovered all the data with r-studio and formatted the drive, everything seems fine, but - win7 doesn't hibernate anymore. I've reinstalled ubuntu, checked the drive flags (boot, active, etc; I've read it could cause such behavior) but it just turns off the screen and that's about it. However, the hibernate.sys files are updated on every drive except the formatted one, where it hasn't even been created. I've been googling it for the past few days but all the advices I've found so far did not help.

I understand that, just as the previous problem, it is not directly related to Ubuntu, but there is a possibility that I messed something up with grub\mbr\etc., so I figured I'd ask here anyway. Thanks!

---

### Post by Mark Phelps on 2013-06-26
A hiberation problem, especially one with Win7, is a very different problem.  People reading the title of this thread won't see the new problem, and won't respond.  You need to open a new thread.

Also, you need to check with the Win7 forums (sevenforums.com) regarding Win7 hibernation problems.  Having GRUB on your PC has nothing at all to do with hibernation.

---

