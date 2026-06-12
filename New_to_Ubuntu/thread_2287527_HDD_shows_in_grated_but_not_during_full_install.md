---
title: "HDD shows in grated but not during full install"
date: 2015-07-20
forum: New to Ubuntu
---

### Post by josh145 on 2015-07-20
Sorry if this is a duplicate post but didn't see it in the search. I have 3 brand new HDD's in a Dell T310 server. BIOS is set to ATA mode. Running Ubuntu 14.04 LTS from live CD I can see the new HDD in grated & able to format to ext3 & mount. Once I try to do the full install, the HDD is not showing up. I'm fairly new to Linux but learning for the Linux+.  Any help would be greatly appreciated.

---

### Post by yancek on 2015-07-20
What is "grated"?
You indicate you have three new hard drives and later state that when you install "the HDD" does not show up.  Do you mean you see none of the three drives? you see two but not the third?  Since you indicate no other operating system, does this mean the computer has no operating system of any kind currently installed?  If that's the case, select the Erase disk and install Ubuntu.  If you have something currently on the computer, the best option to install is the manual option which is referred to as "Something Else".

When you typed "grated", did you actually mean GParted, the partition manager?

---

### Post by buzzingrobot on 2015-07-20
As yancek says, choose the "Something Else" option, which is a euphemism for manual partitioning.  All three disks should be shown.  You can select drives and create partitions as you wish.

---

### Post by josh145 on 2015-07-20
Sorry that was a typo. Yes I meant gparted. Yes all 3 drives are wiped clean of all previous OS's. When I'm in gparted the drives are there & I can format. I am doing all of this from the live CD. When I go to install Ubuntu, after I choose the country & time zone brings me to the "which location to install the OS".  At this stage is where I'm confused b/c the drives not populate.  Am I missing something?

---

### Post by buzzingrobot on 2015-07-20
The presence of other operating systems shouldn't affect the installer's ability to detect the drives.

Partitioning changes may not be picked up without a reboot, so if you haven't rebooted since using gparted, give that a try.

I've always used the 'Something Else' option to specifically put partitions on multiple drives.  Pretty sure the other options assume there's one drive.

---

### Post by josh145 on 2015-07-21
Thank You everyone for the help on this.  I was able to figure it out after some long research.  It seemed that I was not creating the right partition tables when formatting the drives in gparted.  After setting them to the gpt standard my drive was finally showing up & able to install Ubuntu.  Once again, thank you to everyone who helped on this matter.

---

