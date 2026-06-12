---
title: "Dual boot two hard drives"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Don Lockwood on 2008-08-14
Hi Folks,
   I’m just getting started in Ubuntu and already I have a problem, surprise surprise.  To start with I’m using the version 8.04 on a machine that runs a 6G hard drive for Windows XP and a 300G ide that I want to run Ubuntu on.  I created four partitions on the 300.  Partition 1 is for backing up my other computer and is formatted with ntsf.  Number 2 is formatted as Ext3 and holds (I think.) the Ubuntu files.  Number 3 is an Ext3 swap partition. Number 4 started out as an Ext3 partition.
	Problem: After installing Ubuntu on #2 and restarting the machine everything works fine except that #s 2, 3 and 4 did not show up in my computer.  This was true for both XP and Ubuntu.  I expect that the swap partition is hidden but the other two should show. Just for giggles I did a quick format on #4 and made it a ntsf partition.  Result: It is now visible in both OS’s.  I’ve checked the other hard drive partitions and they all seem to be the same size they were before Ubuntu was installed (I can’t see #2) so I feel that Ubuntu is correctly installed on #2.
	Question: should I uninstall Ubuntu reformat 2 and 3 as ntsf and reinstall Ubuntu? Any good thoughts?

Don

---

### Post by GreenN00b on 2008-08-14
#2 will not be visible in xp because xp does not recognize ext3 format by default. If you can boot in ubuntu and you installed it on #2 then #2 is visible as your main file system in ubuntu mounted at '/'.

---

### Post by GreenN00b on 2008-08-14
You should do a google search on how to access ext3 partition from XP, there is a lot of software available that allows you to do this ...

---

### Post by Don Lockwood on 2008-08-14
Hey GreenNoob,
  Thankyou for the quick reply.  I'm still having some problems.  If I go to terminal I can cd back to '/'and see the root files but under Places\computer #2 is not visable.  Since it is not visible I can't mount it nor access it. As I said in my post, #4 also was not visable until I reformatted it as ntsf. Question: will ubuntu install on an ntsf partition?

Don

---

### Post by GreenN00b on 2008-08-14
The alias for #2 in places is File System aka /, the #2 is the main file system in Ubuntu.
Also it is not recommended to attempt to install Ubuntu on NTFS since as far as I known NTFS support is still experimental.

---

### Post by Gannon8 on 2008-08-14
[http://www.fs-driver.org/](http://www.fs-driver.org/)
^ Install the program and follow the instructions. Yes, it will work with ext3.

A 6GB Hard drive? Where did you get that? :confused:

---

### Post by Don Lockwood on 2008-08-14
Thankyou both for the help.  Re 6G hard drive, I build my own confusers and I just happened to have an old HD in my spare parts bin.

Thanks again 
Don

---

