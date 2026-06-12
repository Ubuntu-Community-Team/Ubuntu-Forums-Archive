---
title: "How to delete ubuntu and reinstall?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by lems on 2008-09-28
I need to delete ubuntu and reinstall it. This is the first time I used ubuntu and I think I messed some settings up when trying to install drivers. I get errors all the time and I can never shut down properly.

I installed ubuntu on the same HD as my vista OS on a dual boot setup. I don't have a windows cd with me so I'm not quite sure how to reformat the ubuntu partition. When I boot off the ubuntu cd to try to install ubuntu again, it gives me the option to partition the existing partition that holds ubuntu... I don't want this and I just want to reinstall ubuntu on the same partition it's on. How do I do that?

I have hardy heron by the way.

---

### Post by oilchangeguy on 2008-09-28
> **lems said:**
> I need to delete ubuntu and reinstall it. This is the first time I used ubuntu and I think I messed some settings up when trying to install drivers. I get errors all the time and I can never shut down properly.

I installed ubuntu on the same HD as my vista OS on a dual boot setup. I don't have a windows cd with me so I'm not quite sure how to reformat the ubuntu partition. When I boot off the ubuntu cd to try to install ubuntu again, it gives me the option to partition the existing partition that holds ubuntu... I don't want this and I just want to reinstall ubuntu on the same partition it's on. How do I do that?

I have hardy heron by the way.

use the partition manager in the live cd. delete the ubuntu partition. then reinstall in the unallocated space.

---

### Post by bumanie on 2008-09-28
Choose manual at the partitioning stage and you will be able to choose to format the space presently occupied by ubuntu and reinstall to the same space.

---

### Post by steveneddy on 2008-09-28
> **bumanie said:**
> Choose manual at the partitioning stage and you will be able to choose to format the space presently occupied by ubuntu and reinstall to the same space.

agreed.

---

### Post by kansasnoob on 2008-09-28
> **bumanie said:**
> Choose manual at the partitioning stage and you will be able to choose to format the space presently occupied by ubuntu and reinstall to the same space.

Manual is always the safest bet if you know what you're doing and want full control.

If you're less sure of yourself you could boot the live CD (run without changes to computer) and then go to System > Administration > Partition Editor (gparted) and delete all of your Ubuntu partitions (assuming that's what you want to do), then just leave that area completely unformatted (greyed out) and choose "Guided - use the largest continuous free space" from the partitioner.

Have a look here first:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

