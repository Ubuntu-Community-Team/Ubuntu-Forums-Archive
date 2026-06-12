---
title: "Installing Ubuntu (Again)"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Stoodle on 2008-06-06
Well, I'm reinstalling Ubuntu because my uncle messed it up. However, as I was trying to install, I ran into two problems.

One, After clearing my previous partitions for a fresh start, it gave me three seperate places that free space. Why can't they all be one?

Also, the installer on the 7.04 CD (don't want to download the new one and wait that long) doesn't have the part that allows me to graphically choose the size of my partition.

My last problem is that I actually did install Ubuntu (upset that there was free space just hanging there) but it didn't ask me if I wanted to partition the logical partition! How do I partition it?

On a side note, while I was using the Live CD, it froze up on me. When I went to the first terminal, it was telling me something that it couldn't read when it didn't give me that problem the first time I tried it.

---

### Post by Joeb454 on 2008-06-06
From the Live CD - before running the installer, you could go to System > Administration > Partition Editor, and format all you're partitions there, then run the installer after that :)

---

### Post by Stoodle on 2008-06-06
I guess I didn't look close enough. Thanks man! That's much better. Let's see if this solves some of my problems.

---

### Post by Joeb454 on 2008-06-06
No problem :) If need be - you can erase all your partitions, and then sort them out again, I've done that a few times...

---

### Post by lisati on 2008-06-06
> **Stoodle said:**
> In a side note, while I was using the Live CD, it froze up on me. When I went to the first terminal, it was telling me something that it couldn't read when it didn't give me that problem the first time I tried it.
> **Joeb454 said:**
> From the Live CD - before running the installer, you could go to System > Administration > Partition Editor, and format all you're partitions there, then run the installer after that :)
It might be useful to leave a swap partition behind at the end of the disk, doing so can sometimes help speed up the installation from Live CD. You can always come back later to tidy up the partitions.
> **Joeb454 said:**
> No problem :) If need be - you can erase all your partitions, and then sort them out again, I've done that a few times...
Ditto.

---

### Post by Duck2006 on 2008-06-06
Some info on partitioning that may help.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Stoodle on 2008-06-06
I have my computer partitioned but what about when I'm going to install and it wants me to partition my computer?

---

### Post by Joeb454 on 2008-06-06
You can choose what partitions to mount as / /home etc.

Or you could wipe out the partitions before you install and create them during te install process :)

---

### Post by Duck2006 on 2008-06-06
As Joe454 may be the way to go.

---

### Post by Stoodle on 2008-06-06
What do I do with swap? Where do I mount it?

---

### Post by Duck2006 on 2008-06-06
Put linux swap partition at the end of the drive 1Gb should be bigger enough.

---

### Post by Stoodle on 2008-06-07
Well, what I meant was that I was getting an error saying something about my swap having an incompatible feature or something. I figured it just meant that I hadn't typed something for the mount point. What do you think?

Edit:

what it says is "ERROR!!! File system has an incompatible feature enabled." When I click OK, it says "The test of the file system with the type ext2 in partition #7 of IDE1 master (hda) found uncorrected errors. If you do not go back to the partitioning menu and correct these errors, ythe partition wil be used as is." However, I can't click Continue because it gives me this message again.

---

