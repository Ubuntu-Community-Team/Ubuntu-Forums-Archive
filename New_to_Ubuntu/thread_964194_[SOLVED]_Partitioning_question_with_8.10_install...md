---
title: "[SOLVED] Partitioning question with 8.10 install..."
date: 2008-10-30
forum: New to Ubuntu
---

### Post by AndrewS on 2008-10-30
Hi

I just downloaded the 8.10 iso and made an installation CD, then started a "clean install".  I had in mind to use a 60-odd GB region of unallocated hard drive for the installation; I have XP and 8.04 already on the PC and don't want to lose those installations.  Anyway, when I got to the partitioning step, I got two bars on the screen.  The top one seemed to be a representation of the current state of the disc. showing the unallocated region I wanted to use.  When I clicked the button for "Use largest contiguous space" (or words to that effect) the bottom bar turned green and suggested that 100% of the disk was going to be used for 8.10.  Is this right, was the partitioner going to zap the other partitions?  I'm afraid I chickened out of the installation here and posted this thread.

Thanks

Andrew

---

### Post by JasenGroves on 2008-10-30
While in this step, you should click "Manual", and then the next step will be to break up the partitions. If you already have two partitions ready for Linux (ext2 and swap), then you'll need to set one so that it mounts as "/"

once you have those two, it'll automatically install to the ext2 partition.

---

### Post by AndrewS on 2008-10-30
But won't that lose me the 8.04 installation?

---

### Post by AndrewS on 2008-10-31
I tried again with the alternative install CD, partitioning went fine.  Some other questions, but I'll mark this thread "Solved".

---

