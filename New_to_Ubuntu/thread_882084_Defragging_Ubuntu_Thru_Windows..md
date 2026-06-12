---
title: "Defragging Ubuntu Thru Windows."
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Injeun on 2008-08-06
Hi. I installed 8.04 Hardy Heron on my windows machine. HardyHeron doesn't have it's own partition, but it is accessed thru a boot option. I don't know how that works, but it works great! In fact I'm running it right now.

My query is that when I'm running windows XP, my defragmenter (Disk-keeper) is set to periodically defragment. But Disk-Keeper is now(after installing Ubuntu) showing a gazillion fragments, and I noticed that they were all associated with Ubuntu. It started to defragment but I stopped it and put all the Ubuntu files in the exception list so that it doesn't try to defragment them. I'm afraid it will screw up Ubuntu.

Have I done the right thing? Would it hurt to allow the defragmenter on my windows operating system to attempt to defrag the Ubuntu files? This is my first time here, so I hope this post is in the proper place. Any advice will be appreciated. Thanks.

---

### Post by Blutack on 2008-08-06
Ubuntu creates a few very large files in C:\ubuntu or something similar.  If all Diskeeper wants to do is make those contigous than let it - it may even speed up ubuntu.
If you are worried, copy that folder to a backup and put that on the exclude list.

---

### Post by tech9 on 2008-08-06
> **Injeun said:**
> Hi. I installed 8.04 Hardy Heron on my windows machine. HardyHeron doesn't have it's own partition, but it is accessed thru a boot option. I don't know how that works, but it works great! In fact I'm running it right now.

My query is that when I'm running windows XP, my defragmenter (Disk-keeper) is set to periodically defragment. But Disk-Keeper is now(after installing Ubuntu) showing a gazillion fragments, and I noticed that they were all associated with Ubuntu. It started to defragment but I stopped it and put all the Ubuntu files in the exception list so that it doesn't try to defragment them. I'm afraid it will screw up Ubuntu.

Have I done the right thing? Would it hurt to allow the defragmenter on my windows operating system to attempt to defrag the Ubuntu files? This is my first time here, so I hope this post is in the proper place. Any advice will be appreciated. Thanks.


yes... you don't need to defrag a linux OS - it automatically mounts itself after 30 some odd reboots

---

### Post by halitech on 2008-08-06
sounds like you installed using WUBI.

Honestly I'm not sure how using windows defrag would affect the Ubuntu files but I know in a native system, windows can't even see the drive so it wouldn't touch them. Natively linux does not need to be defragged so probably safest to not allow windows to defrag it.

---

### Post by Locke_99GS on 2008-08-06
If you used Wubi to install linux on an NTFS partition, let it defragment - no harm will come.

Defragging a natively linux filesystem isn't needed.

---

### Post by jkid on 2008-08-06
i dont think need to defrag linux unless you have a disease that make install and unistall PROGRAMS in a daily bases

---

