---
title: "How do I mount my hard drive partition?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by nerd0795 on 2008-05-19
Sorry for making another forum for this... I asked another question and I was waiting quite a while and I gotta finish the install today.

I made a partition from Gparted on the ubuntu live cd.  So I can dual boot Vista and Ubuntu.  I made a partition of 40 gb out of my hard drive.  2 hard drives capacities is about 250 gigs.  

I wanted to know how to select the unallocated space to use.  Found in a tutorial I used before.  He told me to select manual so now I am in a menu and he told me to mount the partition.  I forgot the format name.  Can someone tell me how do to this without losing windows.  Because stupid computer never came with an install disk >.<  Any other things before installing?  

Please do not leave the forum.  I am bound to have a new question posted in thirty seconds.

Can you screen capture in ubuntu live cd?

---

### Post by Victormd on 2008-05-19
When installing, as you mentioned, select manual. You can mount the 40G partition as "/" and format as "ext3". You will also need a partition to set as SWAP, and you can do this from the installer (before creating the 40Gb partition, resize it using the installer so you'll have the extra space for swap). I would set the swap partition to 512MB but others might tell you different (256MB - 1GB).

As long as you don't do anything to the partition where windows is located, you'll be Ok.

---

### Post by nerd0795 on 2008-05-19
Not to be rude.  But can I have it a bit easier.  I'm  kinda confused.

This is what I think I should do:
 
Use Gparted.
Go to my unallocated space and resize it to leave around 600.  Then make the 600 MB a SWAP patition.

Is that right.

---

### Post by Victormd on 2008-05-19
Yes.
You can either use gparted or you can resize during the installation, which ever is easier.
Assuming you're going to use gparted, once you've created the partitions, run the install and when asked about the partitioning method, choose "manual", mount the ~600MB partition as swap (double click to select/edit) and mount the ~39.4GB partition as "/" and format as ext3 (double click to select/edit)

---

### Post by Victormd on 2008-05-19
The install will take care of the rest...

---

### Post by nerd0795 on 2008-05-19
Just created swap partinion.

I selected linux-swap.

and I gave it 600MiB

---

### Post by nerd0795 on 2008-05-19
Do I put SWAP as a primary partion?

because if I try to make the other one it gets mad at me saying I have to many primary partions.

---

### Post by nerd0795 on 2008-05-19
Here is what I did in GPARTED:

I didn't apply yet.  I wanted you to double check it:

/Dev/sda1 ntfs pqservice 6.38GB (for windows)
/Dev/sda2 ntfs ACER      73.20GIB (for windows)
New Partition #1 Extended 40.GB (for ubuntu) (Extended)
      New Partition #2 linux swap 596.16 MB (Logical)
      New Partition #3 ext3       39.42  MB (Logical)
/Dev/sda3 ntfs DATA      112.85GB (Windows)

Is this good?

---

### Post by Victormd on 2008-05-19
Sorry for the late reply...
Well, you can only have 4 logical partitions (I think), that's why gparted didn't let you create it.

Why are you creating "New Partition #3 ext3 39.42 MB (Logical)"? Is this going to be a backup or something like that? (Ubuntu can read/write to NTFS without any problems)
I would probably remove "New Partition #3" and increase your "/Dev/sda3 ntfs DATA 112.85GB (Windows)" Furthermore, I would create "New Partition #1 Extended 40.GB (for ubuntu) (Extended)" as Logical instead of Extended, and "New Partition #2 linux swap 596.16 MB (Logical)" as extended.

Other than that, I'd say go for it, everything looks good.

---

