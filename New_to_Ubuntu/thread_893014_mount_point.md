---
title: "mount point"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-08-17
I'm installing an Ubuntu/Vista dual boot, I'm going through the preliminary steps of the installer and I need to pick the partition I'm installing it on.  I already have a specific partition, which is empty, which I am installing it under.  But I don't know what to pick for the mount point and I don't want to screw anything up.  I'm assuming it is "/", am I correct?

---

### Post by Oldsoldier2003 on 2008-08-17
yes, the / partition is the what you want to choose as mount point for the partition.

---

### Post by echo314 on 2008-08-17
ya. / is the root dir, everything will go there. if you want a slightly different setup, make the / partition about 8 gigs, make the swap whatever, and make a /home partition thats large (where all your data will go). This way, if you reinstall your OS, all your files are settings are preserved.

---

### Post by SalsaShark on 2008-08-17
Hmm, now I have to allocate swap space, how do I do that?

---

### Post by caljohnsmith on 2008-08-18
If you haven't all ready allocated a partition for swap space, you'll need to go back to the partitioning stage and do so. I think the general rule is the swap space should be twice your RAM size.

---

### Post by hotrod6657 on 2008-08-18
When ever i install i always set up my partitions in the partition editor first, and then run the installer.

It's under system and either administrator or preferences on the live Cd (can't remember which)

Open that up and make yourself your main partition, ext3 and swap, i usually do about a gig.

Then when you run the installer and it gets to the partition part hit manual and click edit on the ext3 partition.  Tell it to format to ext3, set the mount point to / and bingo.

The swap should already be set up to be used as swap, but you can check by hitting edit and making sure, no mount point for it.

---

### Post by kansasnoob on 2008-08-18
Look at the section "NEW: Choose one of three different Ubuntu 'Desktop CD' graphical installations," in the following link:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by SalsaShark on 2008-08-19
> **hotrod6657 said:**
> When ever i install i always set up my partitions in the partition editor first, and then run the installer.

It's under system and either administrator or preferences on the live Cd (can't remember which)

Open that up and make yourself your main partition, ext3 and swap, i usually do about a gig.

Then when you run the installer and it gets to the partition part hit manual and click edit on the ext3 partition.  Tell it to format to ext3, set the mount point to / and bingo.

The swap should already be set up to be used as swap, but you can check by hitting edit and making sure, no mount point for it.

So, as it stands right now, I have 4 partitions, sda1, sda2, sda3, and sda4.  Sda1 and Sda 2 are for Vista and recovery, I want Ubuntu to be on sda3 which is already formatted to ext3 and sda4 is formatted for linux-swap.  So when I do the installer and click on Manual in the partition stage, sda1 and sda2 should have "do not use this partition" when I click edit. 
  
Sda3 should say:
use as: ext3 journaling file system
Format: checked (or can this be unchecked since it's already formatted for ext3
Mount Point: /

Sda4 should say:
use as: swap area
and it's unavailable to format or to mount

---

### Post by SalsaShark on 2008-08-19
Bump.  Sorry, I just kind of want to get this done with.

---

### Post by M4rotku on 2008-08-19
That setup sounds good to me.  The only thing that I would change myself would be to create the Vista backup disks and remove the backup partition (sda2) so as to have extra space.  However, if you want the easy backup, then that setup sounds like it would be the simplest thing.

---

### Post by SalsaShark on 2008-08-19
Thanks a lot.

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

