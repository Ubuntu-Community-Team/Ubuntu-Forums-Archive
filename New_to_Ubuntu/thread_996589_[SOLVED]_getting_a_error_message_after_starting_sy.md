---
title: "[SOLVED] getting a error message after starting system"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by avinash389 on 2008-11-29
im gettin ERROR while my sys is doin rotunie check of drivers
it says fsck check of root failed
please can any one help wat happend


after starting system
i'm getting all these .....

checking drive/dev/sda1:8%(stage 1/5,147/1170)
/dev/sda1:Inodes that were a part of a corroupted orphan linked list found.
/dev/sda1:UNEXPECTED INCONSISTANCY ;run fsck MANUALY .
                (ie with out -aor -p options)
fsck died with out exit status 4
checking drive/dev/sda1:9%(stage 1/5 , 153/1170)
*an automatic file system check(fsck)of rootfile system failed.
a manual fsck must be performed then the system system restared
the fsck should be performed in readd only mode
*the root file system is currently mounted in read only mode
a maintaince shell is now been started
after performing the maintance press controll -D
to terminate the maintance shell and restart ...

i'm gettin all these after startin my system ...
please help me as i'm new to linux

---

### Post by nhasian on 2008-11-29
that doesnt sound good.  you'll need to boot off the liveCD and run fsck manually on the partition to fix it.  some data may have become corrupted or you may have a hardware failure.

---

### Post by avinash389 on 2008-11-29
thanks for your reply nhasian.
i'm very new to ubuntu can you please tell me how to run fsck mannually....

---

### Post by Elfy on 2008-11-29
Should be able to do that from the recovery mode as well, the error says that the filesystem is mounted in a state in which the check can take place

> the fsck should be performed in readd only mode
*the root file system is currently mounted in read only mode
a maintaince shell is now been started
after performing the maintance press controll -D

You could have run it from there

fsck /dev/sda1

then ctrl+d would have resumed the startup

---

### Post by avinash389 on 2008-11-29
thank you  forestpixie that solves my problem

---

