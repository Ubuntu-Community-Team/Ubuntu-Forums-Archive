---
title: "Identifying SATA drives in Ubuntu 11.10"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by DBVogt on 2011-11-08
I'm running Windows 7 and installed Ubuntu 11.10 on a 500 gig SATA- C drive. E is another 500 G SATA drive with all my files. I can run Libre and load a DOCX file from E. If I run Libre and click on a "recently found" file from E, Libre says it can't find it. Can I fix this?

I've installed VirtualBox and installed XP under it. XP runs but I've yet to get USB up and running. Instructions in Virtualbox say I have to add a SATA controller to have XP see the second drive. Right now VB just shows the Ubuntu partition as IDE and the VB docs say to specify SATA in Ubuntu so VB can see it. How do I identify the drives in Ubuntu as SATA? 

The E drive is identified  in Dash>File System as /media/c8ec6f2bec6f12cc. (that just rolls off the tongue, doesn't it).

Last question. Can I increase the HD space allotted to Ubuntu after it's installed or do I have to reinstall everything?

---

### Post by audiomick on 2011-11-08
HI.
Firstly, I can't help you with your questions regarding VB, as I have never used it.

As far as the behaviour of Libre goes, I think what is happening there is that the partition with the documents is not permanently mounted. If this is the caes, when you go to the partition in your file manager as you would when you open a file out of its' folder, it gets mounted in the process. If you haven't been there since the computer was started, or if it has been unmounted, and try to get to the file via "last opened", it won't work. I just tried this to be sure... ;)

You should be aware that the way Linux deals with drives and partitions is fundamentally different to windows. Linux does not differentiate, in its' file system structure, between different partitions and drives. You should have a look at this lot.

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Regarding your last question, yes you can re-size your partitions without re-installing.
I should say that a lot of people say to use the windows tool to re-size your windows partition, and everyone says to back up your stuff before you do any partitioning on any type of file system.
Here is some fairly comprehensive reading on partitioning. You will notice that the author maintains that the Linux partitioning tools can safely do windows partitions. Personally, I use the windows tool. It is the one made for the job, and you should start windows a couple of times after you change its' partition to let it sort itself out before you do anything else, so it is no big deal for me if I do the change in windows or in Linux.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

I hope that helps you a bit.

---

### Post by DBVogt on 2011-11-08
Thanks for the reply and the links. I'll check them out.

---

### Post by Mark Phelps on 2011-11-08
If you actually installed Ubuntu in your "C" drive, since that is NTFS, you must have installed using Wubi. That does not use standard partitioning, so you can not use partitioning tools to expand it.

The Wubi Guide, linked below, has instructions on how to resize your Wubi installation:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

As to other partitioning activities, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader or experiment with a real dual boot setup.

As to opening the files on E:, are you hibernating your Win7 setup and then booting into Ubuntu?  If so, when you then go back to Win7 and waken it, you will find the files are GONE. Why? Because Win7 makes a copy of the partition tables when it hibernates, and when it then wakes up, it rewrites the partition tables from the copy it saved -- effectively removing any changes you made while in Ubuntu.

If you are hibernating Win7, then there's no real way to "fix" this because this is how hibernation works.

---

