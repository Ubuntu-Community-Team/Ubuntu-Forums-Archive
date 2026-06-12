---
title: "Dual boot and partitioning"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by groovestorm on 2011-10-02
Hi everyone,

I have a dell inspiron notebook with windows 7. I tried installing Ubuntu but it took forever so I cancelled the installation. I was able to log back into windows and it worked fine. I tried installing ubuntu again, but the partition table had smaller sizes this time. Ubuntu will not install and says I need to go back and make the partitions at least 2.5 gb. I cannot log into windows. The startup manager took forever to find anything so I tried something elses. I took the cd that came with my laptop, which just says it has drivers on it, so I don't know if it has windows or not, and then I loaded it in and restarted with windows. Now the startup manager finds the solutions but it just keeps restarting and then scanning, then telling me to restart again.

Ubuntu is still not completely installed yet. I cannot view youtube or anything because it says it needs me to find a program to open things with. It says so when I try to install adobe flash player, and I do not have anything listed but empty personal folders in ubuntu. If I could get access to my windows stuff again I could back it up and erase windows. There are 2 500 gb drives, one is external and almost full, but then my laptop was half full when I checked. Now ubuntu says there are as fallows:
1.8 GB filesystem
1.7 GB filesystem
1.1 GB filesystem
WD 500 (my external)
Recovery
Dell Utility
542 MB Filesystem
and finally OS

I can access my windows files through Ubuntu, but I don't know what it will be like when I restart again.

I wish I knew what partition to install ubuntu on. Please help I can't use anything but firefox on ubuntu. It is saying that the drive I selected was too small, but in the partition interface I don't know where to select the partition to install on and I don't just want to go ahead with it because I don't want to screw things up even more. Any help will be appriciated.

---

### Post by Mark Phelps on 2011-10-03
These laundry-list-of-problems posts generally do NOT work because the problems tend to be different, as are the solutions.

So, what is it that you REALLY want to do next? You've rattled off a long list of complaints, all of which are different, and it's unclear what your priority next item happens to be.

So, what ONE thing is the most important to have working next?

---

### Post by groovestorm on 2011-10-04
Sorry about the insane post, I know it was long and confusing. I used a backup software to back up all my data onto another HD. I re-installed windows 7 and am going to make a backup of it as well.
 
What I need to know about is the partition tool in the Ubuntu installer. Normally it gives me a slider but now it doesn't. It gives me a list of partitions and I do not know which one is which. I can only guess by the file system and size. I just want to install it on my OS C: along with windows.

---

### Post by garvinrick4 on 2011-10-04
In the Ubuntu live cd (install cd using Try Ubuntu) is a partitioning tool called "gparted"
[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")

Here is a Ubuntu link with "How to" with graphics
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by Mark Phelps on 2011-10-04
The installer gives you a slider when it is able to shrink an existing partition and create a new one in the empty space.

If you already have the maximum of four primary partitions, you can't create any more, so no slider is presented.

To see what you have, open a terminal in UBuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  Post the results back here.

---

