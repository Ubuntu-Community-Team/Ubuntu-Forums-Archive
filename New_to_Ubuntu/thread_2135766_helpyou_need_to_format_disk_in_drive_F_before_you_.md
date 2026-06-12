---
title: "help:you need to format disk in drive F: before you can use it"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by maganga msongo on 2013-04-15
hi,
am beginner of  ubuntu forum  and it is my first post 
i encounter one problem when i transfer data to my external hard disk i remove without safe remove .when i put again i  encounter this  error  "You need to format disk in drive F:before you can use it 
any help please
regards  
my HDD IS TOSHIBA 320GB

---

### Post by ajgreeny on 2013-04-15
How is the disk formatted, fat32, ext#, ntfs?  You may be able to help by attaching it to a windows computer, removing it properly, and then trying again on your ubuntu machine.

However as you talk of the error saying Drive :F, I wonder if you have formatted the disk in ubuntu and are seeing this error in windows.  If so it suggests that you have formatted as ext#, which windows can not read, hence the error message.

---

### Post by Mark Phelps on 2013-04-15
> **maganga msongo said:**
> ... my external hard disk i remove without safe remove .when i put again i  encounter this  error  "You need to format disk in drive F:before you can use it 
any help please
regards  
my HDD IS TOSHIBA 320GB
Any time you do this with a disk containing  a partition formatted for Windows (i.e., NTFS) you are likely to get this message.  The solution is simple -- do NOT just yank the drive out, do safe removal every time.

---

