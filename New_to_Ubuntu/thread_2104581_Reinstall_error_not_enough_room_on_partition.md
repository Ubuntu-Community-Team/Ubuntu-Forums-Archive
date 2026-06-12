---
title: "Reinstall: error not enough room on partition"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by alexgo on 2013-01-13
I'm trying to reinstall Ubuntu because the first installation didn't seem to complete, I think because my computer auto ejected the CD when the computer still needed it.

So when I click the delete ubuntu and reinstall (I'm dual booting windows and Ubuntu), it tells me there is not enough space and has me go to the partitioning. My problem is I don't know what in the world to do there.

When I tried to install the first time it did partitioning for me, so I'm confused as to why suddenly I need to do it manually. It appears I need to delete the previous ubuntu installation( Isn't the option I picked supposed to do this for me?).  

I think ext4 /, ext4 /home, ext4, and swap are the old Ubuntu files, deleting them doesn't seem to be enough, I need simple step by step instructions as I'm a beginner.

---

### Post by audiomick on 2013-01-13
> **alexgo said:**
> I think ext4 /, ext4 /home, ext4, and swap are the old Ubuntu files, deleting them doesn't seem to be enough, I need simple step by step instructions as I'm a beginner.

Yes, that sounds right. You will need to choose each one for re-use. The swap you can just select to mount as swap. The other two will need a mount point, and to be selected to re-format. I take it there is nothing useful in the /home partition as you indicate that this was an install that hadn't been used. If you have anything in the /home that you want to keep, you can re-mount it without formatting.

If this isn't enough info, let us know. Someone will surely be able to help you along.

---

### Post by alexgo on 2013-01-13
The buttons it gives are New Partition Table, Add, Change, Delete, and Revert.  If I do change, the format partition is grayed out. If I delete each one it acts like I haven't done anything (I guess it hasn't done anything as going back and then forward again restores the partitions.)

I'm not entirely sure what you said to do as I've never done this before(it did partitioning for me during the first installation).

---

### Post by alexgo on 2013-01-13
I think I'm supposed to delete each partition and re-create it exactly as it was, I'm getting the info from the change button, but it doesn't say if I should pick "Logical" or "Primary", what should I do for each?

---

### Post by audiomick on 2013-01-13
> **alexgo said:**
> I think I'm supposed to delete each partition and re-create it exactly as it was, I'm getting the info from the change button,

That sounds like it could be right. I'm a bit hazy. The last install was a couple of months back
> 

 but it doesn't say if I should pick "Logical" or "Primary", what should I do for each?

If you are not using a GPT
[http://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")

which sounds like it is the case, you can only have 4 primary partitions. This will not be a problem if you are only installing the three you mentioned. If you want to add any later, though, it might become an issue. Because of this, it might be a good idea to create an extended partition and put the /home and the /swap in there. You can create lots of logical partitions inside an extended partition. I don't recall the exact number, but I think it is something like 64. Point is, if you set up an extended partition now in place of one of the 4 possible primaries, you have room to move later if you need it. Using an extended partition with some or all of your partitions as logical partitions inside it makes no difference at all to your performance, you there is no reason not to use them.

I would put the / on a primary and the /home and /swap as logical partitions inside and extended partition.

---

