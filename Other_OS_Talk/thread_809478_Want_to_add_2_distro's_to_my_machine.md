---
title: "Want to add 2 distro's to my machine"
date: 2008-05-27
forum: Other OS Talk
---

### Post by phread59 on 2008-05-27
Here is what I currently have:

3 hard drives
1 80 gb IDE with Windows XP 64 on it
1 Sata 320gig with Ubuntu 32 bit on it and set as first in bios boot order.
1 329 gig IDE formatted ext3 with 4 partitions. 2 150 gig primarys and 2 5 gig swap partitions.

I want to add both Ubuntu 64 bit and Fedora 9 in the machine.  How should I go about it?  I have a current dual boot working fine with windows.  Grub is configured for this.  

What I want top know is this.  Should I repartition my Sata and add one there or put them both in the 320 IDE?  Or should I cut the partitions down to 75 gig and save 2 for later?  Just looking for suggestions.

I have half an idea how to map this in Grub.  Would love some suggestions on Grub configurations.  Any help will be appreciated.

Mark Shuman

---

### Post by wolfen69 on 2008-05-27
here is one suggestion. you can delete one of the swap partitions. different distros can share 1 swap partition.

---

### Post by dptxp on 2008-05-27
I do not believe in huge / partitions. 10 GB can be good enough for most.
15-20 GB should last a lifetime.

Install the Grub of the 3rd OS in its / partition and use chainload in menu.lst of Ubuntu for 3rd OS. Only once you have edit Ubuntu menu.lst to add the 3rd OS. THen you do not have to copy paste from one menu.lst to other every time you upgrade kernels of any Linux.

---

### Post by phread59 on 2008-05-27
Some additional info I forgot.  I have 2 500gig external HD's for storing most of what I want.  I don't need too much storage on each partition.

I do want sugestions on the mapping of the HD's in grub for my main starting drive.  Right now I have 1&0 mapped for the drive.  What would the mapping numbers for the different distro's be?  Would I be doing 2&0 for the first then 2&1 for the second ect.  Then just add a +1 chainload at the end for each.  This is what I need to know.  I don't want to muck about too much with grub if I don't have too.  I will go back and cut down the size of the partitions to 70 and just leave a total of 10 for the swap partition.

Any thoughts of partitoning the main drive with the current Ubuntu on it?  It is sitting on 320gig.  or should I just leave it be?  Would be nice to have 100 gig or so internal storage for Linux.

Mark Shuman

---

### Post by phread59 on 2008-05-27
Ok I repartitioned the drive.  I now have 3 primary's SDC1,SDC2 and SDC4 and a 5.12 gig swap.  I am about ready to start shooting OS's onto the drive.  Any suggestions on mapping numbers?  I will hold off until I have the info I need on mapping. Any help would be appreciated.

Mark Shuman

---

### Post by dptxp on 2008-05-28
0 for a, 1 for b, 2 for c, .... drives

0 for 1, 1 for 2, 2 for 3 , ........ partitions

e.g.,

for hda2     (hd0,1)
for hdc1     (hd2,0)

for sdb1     (sd1,0)

---

### Post by phread59 on 2008-05-28
I think what I need is this.  For a linux distribution with it's own bootloader in it's own partition the commands would be:

Title "whatever the distro is, ex. Mepis"
rootnoverify("hd#","partition#")
makeactive
chainloader+1

That is what I have come up with from last night's research.  Is this the additions I have to add in grub's lst?   I just want to be sure before I add these to grub.  I hope I have the spacing and syntax right.  I realize you have to hide or map Windows because of it's overbearing need to be first in the pecking order.  I have that nailed just fine.  I just want to add a few distro's to learn with and experience first hand without the limitations of VM ware.  I have 2 primary partitions and 5 logical partitions set up on my hard drive right now ready to go.  Just want the right grub settings and commands to acess them before heading in.  Any seggestions welcome.

Mark Shuman

---

