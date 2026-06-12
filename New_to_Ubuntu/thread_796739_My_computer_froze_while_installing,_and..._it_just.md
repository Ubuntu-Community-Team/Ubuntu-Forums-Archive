---
title: "My computer froze while installing, and... it just kind of spiraled from there. D="
date: 2008-05-16
forum: New to Ubuntu
---

### Post by billybobfred on 2008-05-16
I set up the basics, partitioned the hard drive, and started installing the system. Unfortunately, my computer decided to freeze partway through this, so there's no Ubuntu. The partition is still there, but Windows can't see it-- fine by me, I wasn't going to use those 20GB in Windows anyway.

Now I try installing again. I get to the partitioning step, and I have no clue how I'm supposed to get Ubuntu onto the partition  made before. The guided options don't seem to fit, and the manual process is just confusing. It wants me to make one of the partitions into a "root file system" (I think that's what it's called, I can't remember), which I would gladly do, if only I knew how to do that. Help plx?

---

### Post by tompickles on 2008-05-16
ok... the root partition called / is where everything major sits. basically, create a new partition and in its settings, set the mount point /   file system ext3. also, create a swap (~512mb) which is like virtual ram with teh filesystem linuxswap...... that will do you ok.. if you have a big enough hard disk, you could also create a /home (same way as /) to put all the data associated with user accounts including your files on there --- makes upgrading less risky (STIL PLEASE BACKUP THOUGH!)

---

### Post by billybobfred on 2008-05-16
Okay, I'll try that. (^_^)b

---

### Post by billybobfred on 2008-05-16
Turns out I have some kind of hardware issue that makes my computer freeze whenever I try to do anything of any importance. Thanks anyway.

---

### Post by ace007 on 2008-05-16
You will never see the Linux partition from Windows by default.  Microsoft says no. You'll need a third party app

---

