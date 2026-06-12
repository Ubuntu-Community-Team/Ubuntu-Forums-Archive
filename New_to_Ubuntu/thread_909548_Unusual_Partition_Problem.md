---
title: "Unusual Partition Problem"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by SirSigma on 2008-09-03
Okay, I haven't been able to get any other operating systems running yet because I still have problems trying to manage my partitions.

I'm running a Toshiba Laptop with an external hard drive from Maxtor. The laptop's C drive 40GB free out of 73GB. The external hard drive has 69GB free out of 149GB. And I'm running Windows Vista Home Premium.

Now I went on a journey trying to find out how to dual boot Vista and XP, and if successful, Ubuntu as well. I feel right at this point that it was just wishful thinking. :(

I was recommended to try using GParted on a disc. So I burned it to a DVD disc and ran it in the boot menu. I was honestly kind of shocked at how unfamiliar everything seemed and felt nervous as to whether my computer would be okay. But the guide I had read told me to simply press enter twice and that the interface would come in from there. I never got there because after pressing enter twice it gave me some kind of error message reading that "the graphical environment should have started automatically but unfortunately it did not" then it said something about being "back to the bash!" which left me very confused about that being some kind of new computer slang. They might as well have written "the goose has been crushed by the boulder!" because that made just as much sense.

So I gave up on using GParted on a disc and discovered I could manage partitions from Vista itself (right-clicking computer and going to manage). The partitioning seems to work there by right-clicking an area and selecting "shrink" to create unallocated space.

This is where my problem comes in. If you remember how much memory I had before, that sounds like plenty to run anything. But it only allowed me to shrink down 21MB worth of free space on my C drive. Yes, I typed that correctly: 21MB. I have so much free space on the drive but it just told me that I could only set 21MB aside as unallocated space.

I went to my external hard drive to create a partition and I encountered a similar problem. Out of all that free space, it only allowed me to set 50MB aside for free space. I'm really confused about this.

I then tried defragmenting my C drive, but when I went back to the partition managing area in Vista and the space dropped from 21MB to 0MB.

I'm currently at a complete loss as to what to do next. I really need help.:confused:

---

### Post by ubername on 2008-09-03
> **SirSigma said:**
> Okay, I haven't been able to get any other operating systems running yet because I still have problems trying to manage my partitions.

I'm running a Toshiba Laptop with an external hard drive from Maxtor. The laptop's C drive 40GB free out of 73GB. The external hard drive has 69GB free out of 149GB. And I'm running Windows Vista Home Premium.

Now I went on a journey trying to find out how to dual boot Vista and XP, and if successful, Ubuntu as well. I feel right at this point that it was just wishful thinking. :(

I was recommended to try using GParted on a disc. So I burned it to a DVD disc and ran it in the boot menu. I was honestly kind of shocked at how unfamiliar everything seemed and felt nervous as to whether my computer would be okay. But the guide I had read told me to simply press enter twice and that the interface would come in from there. I never got there because after pressing enter twice it gave me some kind of error message reading that "the graphical environment should have started automatically but unfortunately it did not" then it said something about being "back to the bash!" which left me very confused about that being some kind of new computer slang. They might as well have written "the goose has been crushed by the boulder!" because that made just as much sense.

So I gave up on using GParted on a disc and discovered I could manage partitions from Vista itself (right-clicking computer and going to manage). The partitioning seems to work there by right-clicking an area and selecting "shrink" to create unallocated space.

This is where my problem comes in. If you remember how much memory I had before, that sounds like plenty to run anything. But it only allowed me to shrink down 21MB worth of free space on my C drive. Yes, I typed that correctly: 21MB. I have so much free space on the drive but it just told me that I could only set 21MB aside as unallocated space.

I went to my external hard drive to create a partition and I encountered a similar problem. Out of all that free space, it only allowed me to set 50MB aside for free space. I'm really confused about this.

I then tried defragmenting my C drive, but when I went back to the partition managing area in Vista and the space dropped from 21MB to 0MB.

I'm currently at a complete loss as to what to do next. I really need help.:confused:

It looks like you are only being allowed to resize/ repartition unused 'crumbs' of your disks (which would make sense if you are running the Vista disk manager from within Vista booted from the same disk, if that makes sense!.)

Try running gparted from one of the ubuntu install CD's (You don't mention which version of ubuntu you are trying to install). In other words, boot the machine from the install CD and select the option 'try ubuntu without changing my computer' (or similar) then go to 'Applications' menu and select the 'Accessories' option and select the 'terminal' option. from there type 'gparted'. From there you should be able to select your hard drive(s) and repartition them. If you have problems, make sure that the drives are unmounted (gparted lets you do this, but I can't recall the exact GUI sequence.)

This should let you resize etc. as you wish.

---

### Post by bodhi.zazen on 2008-09-03
IMO you should not use the windows partitioning tool, it is crude at best (as you can see).

Second you should not be playing with these things if you do not understand the terminology.

So, start here : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

You should always, always, always back up any data you do not wish to lose. partitioning your hard drive *usually* goes without any problems or data loss, but one wrong click of the mouse can be a disaster.

Next, perhaps most important, DEFRAGMENT your partitions (from within windows).

Last, fire up the Ubuntu desktop CD and manage your partitions with gparted.

Documentation: [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

If you have problems booting the Ubuntu CD that is indicative you have some hardware issues you will need to solve before you can run Ubuntu. Hardware problems are obviously difficult for even experienced users , but we will try to help.

Keep in mind, Ubuntu is not a drop in replacement for Windows and there will be a learning curve as you explore a new OS.

---

### Post by nadoudidou on 2008-09-03
Hello there

I Have got quite a similar problem.

I have shut ubuntu down after it became unstable. Trying to open apps but none would pop up.

At the next boot I'v got the bash (showing some errors like "command not found") and saying that the root directory is read-only!

I use this computer for work (I'm a translator and all my family income depends on my data, only some of it is saved).

I'm living a nightmare. There must be a solution to this.

I thought I could boot from a live CD and back my files. But is this *very annoying bug* fixable?

Please, kindly, HELP.

---

### Post by bodhi.zazen on 2008-09-03
Yikes ...

First , stop running your computer from hard drive and boot a live CD. You can then look at your hard drive and try tools to recover such as testdisk, photorec, or fsck ...

You may well need professional (data recovery) assistance ...

---

### Post by greco8523 on 2008-09-04
When recovering your data you will want to be careful not to overwrite anything. Testdisk should definitely help in this case. 

This link should help as a guide for you: 
[http://www.datarecoveryadvice.org/](http://www.datarecoveryadvice.org/)
[http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)

---

### Post by SirSigma on 2008-09-06
Thank you so much for replies.

Anyway, I borrowed a friend's external hard drive after booting Ubuntu (the version I'm using is 8.04.1) from the disk without changing my computer. I absolutely fell in love with the interface, and the speeds that Ubuntu accomplishes tasks compared to Vista.

I'm cutting and pasting my things onto my friend's external hard drive as backup (his external hard drive is larger than mine) and I'm going to have my regular external hard drive empty. The transferring is still going right now (it's going to be awhile) and then I plan to partition the hard drive and make a clean install of Ubuntu there. After seeing Ubuntu in action, I don't really care about getting XP to work anymore.

I'll post here again if I'm having any problems. Until then I'm going to take Ubername's advice. Thank you all so much.

---

