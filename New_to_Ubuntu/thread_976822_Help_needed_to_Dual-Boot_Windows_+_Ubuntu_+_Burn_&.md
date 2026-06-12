---
title: "Help needed to Dual-Boot Windows + Ubuntu + Burn &gt;4GB .iso's"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by josephpford on 2008-11-09
Hello all,

Thank you all so much for your assistance with the newbies (me included).

I am looking to dual-boot Ubuntu and Windows XP.  I would like both OSs to be able to read and write from a data partition that will need to be able to store files larger than 4GB (i.e. Fat32 won't work).  I know there is an NT reader for Linux and I know there is an ext2 reader for Windows.  What would you recommend I do, any why?  

250GB total disk space.  Would prefer 50G for both OSs, plus 150G for data.

Thanks,
Joseph Ford

---

### Post by randy78 on 2008-11-09
NTFS... download the GParted ISO [HERE]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779")

---

### Post by josephpford on 2008-11-09
Thank you for your reply.  I have a couple of clarification questions.

1. Why would I want to download the GParted ISO when GParted is already installed on Ubuntu 8.10 Live CD?

2. I assume you mean by "NTFS" that my "data" partition should be NTFS.  Can you please let me know why you think this is my best option?

Thanks again for the reply.

Regards,
Joseph Ford

---

### Post by igknighted on 2008-11-09
Windows can read/write to ext2/3 if you install the right drivers (google ext2fs), I'd use that for data partitions.  Also, to burn >4gb ISO's you need dual layer DVDs and a burner capable of writing them.

---

### Post by randy78 on 2008-11-09
Well, you most certainly can use the version of GParted that's included on the LiveCD.

As per your second question, both Ubuntu and Windows can read/write to and from NTFS.

[Click here for more info on NTFS]("http://www.ntfs.com/ntfs_vs_fat.htm")

---

