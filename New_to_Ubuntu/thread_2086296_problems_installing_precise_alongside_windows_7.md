---
title: "problems installing precise alongside windows 7"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by mark allyn on 2012-11-20
Hello everyone,
 
I am trying to install 12.04 alongside 32-bit Windows 7.  I begin by shrinking the Windows 7 partition, and this appears to be successful.  After exiting the Windows disk manager I restart Windows 7.  It restarts without a problem.
 
Next, I insert a live CD with 12.04 on it and restart the computer. When I reach the window that asks me what I want to do,  I select "something else" and get a screen that shows the partitions available on SDA.  Now the problem shows up.  The free space is identified as "unusable" by Ubuntu and even when I highlight the line and press "add" the system is unresponsive.  Moreover, the Ubuntu "free space" is about 6 GB larger than the "unallocated" space shown by the Windows disk manager.  
 
Can someone suggest what I should do to solve this problem?  I've hunted around the internet without any luck.
 
Cheers,
Mark Allyn

---

### Post by Impavidus on 2012-11-20
The 6 GB difference may be caused by the difference between gigabytes of 1024^3=1073741824 and gigabytes of 1000^3=1000000000 bytes. The fact that the space is unusable is most likely caused by the fact that you may already have 4 primary partitions on your disk. 4 is the maximum, so you cannot create a new partition unless you replace one of the existing partitions with an extended partition. Can you check how many partitions there are on your disk?

---

### Post by mark allyn on 2012-11-20
Hi Ambividus,
 
Thanks for responding.  Yes indeed the disk has 4 partitions, as you surmised.  So, if you are up to it, could you explain how to modify one of the partitions to make it available for Ubuntu without actually making the Windows piece unusable by Windows.
 
I am unclear as well as to how to use WUBI--or how it is different from--what I have been trying to do.
 
Thanks for the bit about the 6 GB discrepancy.  Very interesting.
 
Cheers,
Mark

---

### Post by mark allyn on 2012-11-20
Hi again, Impavidus.
 
Sorry I messed up your name!  Did it from memory, and I'm getting to be too much a relic to rely on my faulty cortex.
 
Cheers again,
Mark

---

### Post by Impavidus on 2012-11-20
Well, I don't know much about changing partitions in windows (changing windows partitions works best using windows tool), but have a look here: [http://askubuntu.com/questions/161475/how-to-change-primary-partition-to-extended-without-formatting](http://askubuntu.com/questions/161475/how-to-change-primary-partition-to-extended-without-formatting)

Maybe someone else knows more.

(And make sure you don't create dynamic partitions. Windows is very eager to do that, but Linux can't work with them and it's hard to undo a conversion to dynamic. I learnt it the hard way.)

Edit: Click on some of the "Related" links in the lower right of the link I gave. There's some useful information in them.

---

### Post by buffalopike on 2012-11-20
hey mark
perhaps pop in gparted and create the partiton prior to 12.10 install?
just a thought

---

### Post by Mark Phelps on 2012-11-20
> **buffalopike said:**
> hey mark
perhaps pop in gparted and create the partiton prior to 12.10 install?
just a thought

Did you MISS the part where the OP said they already had the limit of 4 partitions?  That being the case, they obviously, can't just create another one!

---

### Post by Mark Phelps on 2012-11-20
> **mark allyn said:**
> Hi Ambividus,
 
Thanks for responding.  Yes indeed the disk has 4 partitions, as you surmised.  So, if you are up to it, could you explain how to modify one of the partitions to make it available for Ubuntu without actually making the Windows piece unusable by Windows.
 
I am unclear as well as to how to use WUBI--or how it is different from--what I have been trying to do.
 
Thanks for the bit about the 6 GB discrepancy.  Very interesting.
 
Cheers,
Mark

Since you want to dual-boot with Win7, please read through the details below ... (presuming one of the partitions is named HP_TOOLS):

Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by mark allyn on 2012-11-20
Hi Mark Phelps,
 
I have read your response and it seems to me that what you are suggesting is the way to solve this issue, short of simply installing Ubuntu as the OS and not trying for an "alongside" installation.
 
Using WUBI I have installed Ubuntu "inside" windows and it seems to function acceptably.  But, I would like to have Ubuntu in a separate partition.
 
In subsequent internet searches I found a contributor who had detailed a solution that used an over-write of the "recovery partition" (preceded by a backup of the recovery partition).  This yields approximately 15 GB of space for Ubuntu.  It wasn't clear how to expand the space from what I read.  I suppose it would entail getting into MSFT's disk manager and shrinking the C:\ partition and then going back into (perhaps) gparted and expanding the "recovery partition"?  Or something of this sort....
 
A pity that HP/MSFT decided in Windows 7 to use up all 4 primaries!  On an older XP machine only two of the primaries were used....Would it be presumptuous of us to figure that this move was a way to retard the spread of Linux distros?
 
Cheers and thanks,
Mark Allyn

---

### Post by buffalopike on 2012-11-21
> **Mark Phelps said:**
> Did you MISS the part where the OP said they already had the limit of 4 partitions?  That being the case, they obviously, can't just create another one!

Yes **I did** miss it. Please accept my most sincere apologies!!!
Was the Win7 partiton defraged before you resized it?

FYI
Perhaps attached screenshot can help?
Just a thought my friend.

---

### Post by mark allyn on 2012-11-21
Hello Buffalopike,
 
I'm assuming you were asking me (and not Mark Phelps) about defragging the Win 7 partition.  The answer is NO, I didn't.  I shrank the C:\ partition in half, but didn't defrag.
 
Cheers,
Mark Allyn

---

### Post by buffalopike on 2012-11-22
> **mark allyn said:**
> Hello Buffalopike,

The answer is NO, I didn't.  I shrank the C:\ partition in half, but didn't defrag.
 
Cheers,
Mark Allyn

As I understand it not doing so ***can ***cause problems.

[http://bit.ly/Uhb61n](http://bit.ly/Uhb61n)

**Happy Thanksgiving!!!**

---

