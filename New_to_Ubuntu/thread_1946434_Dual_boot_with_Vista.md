---
title: "Dual boot with Vista"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2012-03-24
I need some 11.10 installation help here.

I'm looking to create a dual boot between Windows Vista and Ubuntu 11.10. I attempted to shrink my Vista partition by around 100gb on my 250gb HDD, but inside of the Windows partition manager, it said I only had 38gb available to shrink the volume.

I looked around and saw that I needed to either boot into safe mode or use a 3rd party program to partition. Safe mode didn't work at all, as my computer just restarts as soon as the safe mode login screen comes up.

So I'm thinking I could just use GParted, but I realize this will break my windows install in some way. I do have the Vista install CD, and I'm assuming it has some sort of repair option for the Vista installation. Is this my only option right now, to use GParted to create my partition for Ubuntu, and repair the Windows install after that?

And knowing Vista, I'll probably have to use EasyBCD or something like that to fix the MBR mess.

---

### Post by Bucky Ball on 2012-03-24
Before shrinking a Windows partition defragment and defragment again! Windows spews data all over the partition so without defragmentation you will get a reasonably inaccurate report about how much you can shrink.

Always shrink Windows partitions with Windows software; NOT Gparted.

To fix the boot problem you could try Boot-Repair, which is in the repositories or available to download to a bootable disk, or Super Grub Disk.

---

### Post by Thrashrokz33 on 2012-03-24
I've already defragged with SmartDefrag multiple times, to the point where my fragmentation rate is only at 0.3%, which I'm guessing is very low. The Vista defrag included in Admin tools is so painfully slow that I don't even bother with it.

So if I can't use GParted, and I can't shrink the volume to my desired size, what do I do?

---

### Post by mörgæs on 2012-03-24
Changed the title to a more informative one.

---

### Post by Thrashrokz33 on 2012-03-24
Is this a good 3rd party partition software to be used inside Windows?

[http://download.cnet.com/EaseUS-Partition-Master-Home-Edition/3000-2248_4-10863346.html](http://download.cnet.com/EaseUS-Partition-Master-Home-Edition/3000-2248_4-10863346.html)

---

### Post by Bucky Ball on 2012-03-24
Pretty sure you can shrink Vista with its own software inside Device Manager from memory ...

---

### Post by Mark Phelps on 2012-03-25
The only SAFE utility to use from INSIDE MS Windows to shrink a Vista/Win7 OS partition is its own Disk Management utility -- which, as you've discovered, can severely limit the shrinkage.

EASEUS Partition Master is a good tool -- but you'll need the Boot CD version as you'll have to be outside of MS Windows when you shrink it.

Another good tool is the free version of Partition Wizard -- and you can download a burn a Bootable CD of that to use.

---

### Post by Thrashrokz33 on 2012-03-25
Are you sure EaseUS can't be used inside windows to partition? I downloaded it, and it looks like I can just resize it from inside Windows, without making a CD for it.

---

### Post by Mark Phelps on 2012-03-26
__> **Thrashrokz33 said:**
> Are you sure EaseUS can't be used inside windows to partition? I downloaded it, and it looks like I can just resize it from inside Windows, without making a CD for it.

Don't actually know as I have not used it.  I know Win7 Disk Management can resize its own OS partition -- but it reboots in order to do that.

Perhaps EASEUS does the same.  Only way you can tell is to try it.

---

### Post by Derek Karpinski on 2012-03-26
The problem with most windows defraggers is they operate inside windows after it's booted up.  Windows has files all over the place, and a lot of them are unmovable once windows has started.
 
I found 'perfect disk' by raxco to do the best job.  It defrag, then reboot, and finish defragging before windows boots.  It worked great. [http://www.raxco.com/](http://www.raxco.com/) They have a 30 day free trial.
 
When you're done defragging, then go ahead and resize with the windows disk management tools.
 
After resizing, reboot into windows a few times before installing Ubuntu.

---

### Post by hanzj on 2012-03-27
> **Bucky Ball said:**
> Before shrinking a Windows partition defragment and defragment again! Windows spews data all over the partition so without defragmentation you will get a reasonably inaccurate report about how much you can shrink.

Would love to hear from others whether defragmenting twice in a row is better than just defragmenting once.

I ran Disk Defragmenter (Windows 7 computer) and the result was 0% fragmentation. Why would I need to defragment immediately after?

---

### Post by Mark Phelps on 2012-03-27
> **hanzj said:**
> Would love to hear from others whether defragmenting twice in a row is better than just defragmenting once.


Defragmentation, while useful, is not entirely the problem.  MS Windows writes files to the "end" of its OS partition.  While defragging moves some of the files, there are others that simply will not budge.  It's these latter files (which includes, I believe, the MFT) that cause the shrinkage problems.

If you're determined to shrink the OS partition, then look into using either Partition Wizard, EASEUS Partition Master, or MiniTool Wizard v7.  ALL of these can be downloaded for free and will work on Win7 filesystems.

---

