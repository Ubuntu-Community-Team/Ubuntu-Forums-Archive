---
title: "[SOLVED] What is difference of Free space and Available space"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Masoris on 2008-05-28
When I check my hard disk; how many hard disk space left. I open "System Monitor" and open "File System" tab. But there are two numbers on it; one is "Free space" and other is "Available space", I wonder what is difference of them?

---

### Post by quelx on 2008-05-28
Clusters available * cluster size vs (total space avaliable - total space used)

a more detail explanation:

[http://www.forensics-intl.com/def6.html](http://www.forensics-intl.com/def6.html)

---

### Post by Masoris on 2008-08-10
I could write more file when available space is 0 on my ext3 filesystem. What happened?

---

### Post by Vivaldi Gloria on 2008-08-10
> **Masoris said:**
> I could write more file when available space is 0 on my ext3 filesystem. What happened?

I guess the system monitor rounds the numbers. So it wasn't exactly 0.

---

### Post by Masoris on 2008-08-10
> **Vivaldi Gloria said:**
> I guess the system monitor rounds the numbers. So it wasn't exactly 0.

I don't think so, I could write a file until "Free space" become 0. So what is "Available space"?

---

### Post by Masoris on 2008-08-11
I found answer by googling. It is because 5% of disk space is reserved for root user. I could change this percent by *tune2fs*.

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space)

---

### Post by Vivaldi Gloria on 2008-08-11
> **Masoris said:**
> I found answer by googling. It is because 5% of disk space is reserved for root user. I could change this percent by *tune2fs*.

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space)

Good find there.

---

### Post by mcduck on 2008-08-11
I wouldn't recommend changin the reserved space a mount on root file system. For all other partitions it's OK.

(If you set it to too small amount on /, and then accidentally manage to fill the disk, you won't be able to boot the system at all any more..)

---

