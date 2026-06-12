---
title: "NTFS drive shows empty"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by max renn on 2008-04-29
put good NTFS 160GB HD in K7.10, was working for two weeks, shared on network, etc.  Now shows up as empty with 7 of 9 GB free.  Pull drive and put in windows box and the 160GB shows up fine, 140GB used.  Ran chkdsk and OOdefrag and no issues.  Back to Linux and same issue.

Any ideas on how to make this work?  I have two other NTFS drives in K that read fine.

---

### Post by max renn on 2008-04-29
OK, I figured it out.  It was not mounting anymore (mount at startup unchecked),  reboot and fine.  

So what the heck caused this?  It has worked through numerous reboots over the past two weeks.  And why could I see the drive at all if it was not mounted?  And why could I see the same 7 of 9 GB free over the network from a windows box?

---

