---
title: "[SOLVED] JSF - Error: Cannot open device /dev/sdc1"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Thee_Baron_ on 2008-07-11
Hello, recently made a thread about making my data only hard drives ext3 - after looking over some other filesystems I was thinking about going with XFS, but then noticed that JFS is nearly just as good but offer low CPU usage (which is what I really want).

So after swapping data to another HDD I formatted it to JFS and it mounted fine, no error or anything. So then I transferred the data back to the JFS and formatting that drive. Now I cant mound the drives! So I cant access the data :(

This is what the warning message says in GParted:
> 
jfs_tune version 1.1.11, 05-Jun-2006

Error: Cannot open device /dev/sdc1.

jfs_debugfs version 1.1.11, 05-Jun-2006
[0020]%G

Error: Cannot open device /dev/sdc1.

Unable to read the contents of this filesystem!
Because of this some operation may be unavaiable.

Please help!
Thanks.

---

