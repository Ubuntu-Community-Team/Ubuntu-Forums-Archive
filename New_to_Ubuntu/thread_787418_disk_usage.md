---
title: "disk usage"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by ayu on 2008-05-08
Hello, Trying to burn a file in k3b (with create image first) reports not enough diskspace, while I'm looking at Conky and it says 71.37/78.77 GB used. Nautilus reports that my home folder has 3.4 GB free. df reports 74837356/82597208 1K-blocks used, but only 3564080 available. How come my 'available' does not equal total minus used? Thanks!

---

### Post by NightwishFan on 2008-05-08
Possibly because ext3 has a reserve of diskspace about 5%, to prevent fragmentation.

---

### Post by ayu on 2008-05-08
Thanks, did not know that ext3. I guess the question now becomes: How do I get conky to display the (used+available) instead of (total)?

---

### Post by zach382 on 2008-05-08
> **ayu said:**
> Thanks, did not know that ext3. I guess the question now becomes: How do I get conky to display the (used+available) instead of (total)?
 
Hmm try looking in here: [http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")

These variables might work. fs_used (File system used space ) and fs_free (Free space on a file system available for users. )

---

