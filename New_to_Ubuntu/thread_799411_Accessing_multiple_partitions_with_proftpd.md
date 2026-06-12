---
title: "Accessing multiple partitions with proftpd?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by dreadh3ad on 2008-05-19
How do I set up proftpd to allow a user to access multiple partitions?  
I tried to create a symbolic link to the other partition but got this error:
"550 upload2: No such file or directory"

---

### Post by rockerphil on 2008-05-19
have you got all the partitions mounted? cus if not you can't link anything to a file/partition that isn't on your file system

---

### Post by dreadh3ad on 2008-05-19
The partition is mounted correctly.

---

### Post by rockerphil on 2008-05-19
then it may be a permissions issue, are you trying to allow another user on your machine access to the partitions? if so then it might be because you're mounting the partition to your home folder perhaps? which may cause the file to be unaccesable to other user accounts. if this is the case i'd pull up a terminal and change the file permission

sudo chmod +r <partitionmountpoint>

---

