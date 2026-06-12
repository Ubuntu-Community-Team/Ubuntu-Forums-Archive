---
title: "Partition Trouble...Need Advice"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by jpr13 on 2008-05-11
I have a new HP Pavilion dv9825 laptop that came with Vista. Using Vista I shrank the ntfs partition then installed 64-bit Hardy. I left a 100 gig area unpartitioned so I could create a data partition later that windows and hardy could both access. 
My problem is that I knew I can only have 4 primary partitions so I thought the swap, hardy root, vista and data would be the 4. Vista came with a D: drive for system restore. I did not erase it so now I can't make my data partition. I should have realized this when I was installing but I didn't.

So, should I...

1. Just erase the system restore part?
2. Expand the system restore and put a data folder in it, would that work?
3. Any other ideas?


Thanks in advance
Jason

---

### Post by diablo75 on 2008-05-11
The 4 partition limitation (I'm pretty sure) is a software barrier enforced by Microsoft, but not by God himself.  I think you should be able to use a gParted Live CD to create the partition you are wanting.  Download the ISO image here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

