---
title: "shrinking ubuntu partition"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Mr Pockets151 on 2008-05-23
I did a google search on the subject and found many hits. Nothing really explains anything though.  I download the Gparted Live CD and plan on using this.  I have my ubuntu set up on it's own IDE drive.  Except when I did the fresh install I used entire disk because I couldn't figure out how to do the manual set up.  This is a dual boot system, with XP on a SATA drive.  Grub is configured properly at this point.  

My option is to do a fresh intall of ubuntu and want to use only 80 GB of my 250GB IDE drive.  However I don't quite understand how manual partitioning works and what to make of the swap file. I don't see how I can select an 80 GB partition only.  

Second option would be to use Gparted and shrink the ubuntu partition.  But will this screw up my GRUB/menu.lst file?  I plan on using the free space for a mandriva install.

---

### Post by stchman on 2008-05-23
> **Mr Pockets151 said:**
> I did a google search on the subject and found many hits. Nothing really explains anything though.  I download the Gparted Live CD and plan on using this.  I have my ubuntu set up on it's own IDE drive.  Except when I did the fresh install I used entire disk because I couldn't figure out how to do the manual set up.  This is a dual boot system, with XP on a SATA drive.  Grub is configured properly at this point.  

My option is to do a fresh intall of ubuntu and want to use only 80 GB of my 250GB IDE drive.  However I don't quite understand how manual partitioning works and what to make of the swap file. I don't see how I can select an 80 GB partition only.  

Second option would be to use Gparted and shrink the ubuntu partition.  But will this screw up my GRUB/menu.lst file?  I plan on using the free space for a mandriva install.

Load up the Ubuntu LiveCD and fire up Gnome Partition Editor.

Select the drive on which Ubuntu is installed.

Tell gparted to turn off the swap file.

Right mouse click and select resize.

Click apply.

You will now be left with free space.  Create a new partition in the free space selecting whichever file system you like.

Select apply.

Pretty simple.

Here is a good site:

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Mr Pockets151 on 2008-05-23
Thanks for the reply.  What is the reason to disable the swap file. ?  Do I turn it back on when I'm finished resizing.

---

### Post by stchman on 2008-05-23
> **Mr Pockets151 said:**
> Thanks for the reply.  What is the reason to disable the swap file. ?  Do I turn it back on when I'm finished resizing.

In order to resize a partition a swap file cannot be active.  Ubuntu will turn the swap file back on.

---

### Post by logos34 on 2008-05-23
> **stchman said:**
> In order to resize a partition a swap file cannot be active.

hmm, I didn't know that. Why have I never encountered this issue (done lots of resizing too)?

---

