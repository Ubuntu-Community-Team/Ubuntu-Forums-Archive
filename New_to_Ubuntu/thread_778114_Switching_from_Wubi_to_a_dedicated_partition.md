---
title: "Switching from Wubi to a dedicated partition"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by tentel on 2008-05-01
I just tried out the new Wubi feature and I think it is great.

However, I am hesitant to begin working in earnest on getting my Broadcom wireless card to work.
I would like to eventually make Ubuntu my only OS, and once I can get the internet to work reliably, I'd like to begin to make the switch from Vista.

I am just worried that once I get everything working in Wubi, I'll have problems switching over to a dedicated partition.
I've been reading that the LVMN does not currently support 8.04, and I've read some alternate ways to make the switch, but I'm worried that I won't be able to transfer over the settings that would keep Ubuntu from being broken.



Since I am definately planning on making a dedicated partition, should I even bother starting off with Wubi?
I'd like to make separate /root and /home partitions, so I don't even know if that would be possible when switching from Wubi.



-Tim

---

### Post by Tatty on 2008-05-01
Do you mean LVM as in logical volume management? If LVMN is something different then im afraid i dont know what that is, but if you do mean LVM then it definately is supported in ubuntu.  Though it is not included as an option in the live CD - you will have to use the alternative CD to install.

I would also recommend installing straight to a new partition if you are planning to do this anyway.  Just make sure you backup and defrag your windows partition 3/4 times before installing.

---

