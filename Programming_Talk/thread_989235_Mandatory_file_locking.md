---
title: "Mandatory file locking"
date: 2008-11-21
forum: Programming Talk
---

### Post by nightwatchman on 2008-11-21
Hello,

I need to put a mandatory lock on /dev/fb0 (presently any file) in Linux OS. But in actual scenario it will be a device file.

Scenario:
1. Process A is super process
2. Process B is normal process.
3. Process A and B are non-cooperating process (So, advisory locking is out of scope). 
4. At particular instance Process B is accessing /dev/fb0.
5. Now, Process A wants access to it.
6. Process A locks /dev/fb0
7. It can hold the lock as long it wants & in any case process B cannot write anything to it. (It’s better if B cannot read the contents also).

I also changed permissions of directory and lock file.

directory:
drwxr-Sr-x 2 ists ists   4096 2008-11-21 11:20 test

file to be locked:
-rw-r-Sr-- 1 ists ists   15 2008-11-21 09:32 lock.txt

uname -a:
Linux ists-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

Please help me how to achieve above or what all I need to do it.
I am really stuck.

Regards,
~Nick

---

### Post by mawe3661 on 2008-12-03
I was going to post a question wether mandatory locking works at all on Ubuntu. There are a few requirements that need to be filled. The partition needs to be mounted with mand in fstab etc. However, even when following guides I have not been able to get it to work. Maybe its a feature lost in history?

---

