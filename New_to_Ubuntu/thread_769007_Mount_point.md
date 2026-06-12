---
title: "Mount point?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Kymeia on 2008-04-26
I'm installing using the CD but it's partitioning the disk and asking me to decide on a mount point - too many options - what do I put?

---

### Post by Can+~ on 2008-04-26
On the installation?

Once you select the correct partition you want, it will be mounted on "/" (without the " " of course), it's a single slash, it's the "root folder" of linux system.

You could also set a "SWAP" partition if your ram is old, if you have more than 1gb of ram, you don't need it actually.

---

### Post by Joeb454 on 2008-04-26
If you are unsure then you may be better off installing using the Guided partitioning method :)

---

### Post by Kymeia on 2008-04-26
ah good - that's what I'd guessed but why the other options then?

---

### Post by PattonPending on 2008-04-26
Is this a clean, new install or are you trying to preserve information on the system?

Mount points are the directory locations in linux where you want to find certain partitions.

So if you want a partition to be the root directory (roughly equivalent to C:\ in windows) then you should set its mount point to "/".  If want to find other partitions in specific places, you can select their mount points as well.

If you give a bit more information about your circumstances I can probably help more.

---

