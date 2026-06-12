---
title: "no of processes and states"
date: 2010-05-03
forum: Programming Talk
---

### Post by coolkiller on 2010-05-03
hey !!!
 
i want to know all the number of processes runnig or sleep and with their states ...cud any one help me ..

---

### Post by Dayofswords on 2010-05-03
'top' command displays that info on the second line

EDIT: oh this is "programming talk", this may not be what your looking for...

---

### Post by coolkiller on 2010-05-03
thanx for reply
i want to print these pcocess names ,their states,the processes made them on waiting and cpu utilization through a program in jcc i mean c language...

---

### Post by rnerwein on 2010-05-03
hi
you are familar with C programming ?
then you need: opendir, readdir, read --> in /proc/PID/stat you will find every thing you need ( you can geather much
more information about processes there )
see: man 5 proc for further information.
have fun

ciao

---

