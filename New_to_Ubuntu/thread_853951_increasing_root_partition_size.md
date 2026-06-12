---
title: "increasing root partition size"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Samrat Rao on 2008-07-09
i have ubuntu 7.10 installed in my system. pl tell me how to increase my root partition size. i have gparted with me. i have allocated space contiguous to the root partition. also will this operation affect my ubuntu installation?

---

### Post by Elfy on 2008-07-09
You need o resize oneof the other partitions so ther is unallocated space, then move partitions so that unallocated is next to the root partition. Then you can add the unallocated to the root partition.

You have to use gparted on the livecd or use a bootable partition editor.

It shouldn't affect your ubuntu installation, but there is alwyas the possibility of something going wrong so make sure you have backups of anything you can't afford to lose.

---

