---
title: "problems installing ubuntu?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by rm2011 on 2008-10-31
Hi,
I am trying to install xubuntu on an older laptop.  I made a live cd, but whenever i try to boot from the disk after about 7 minutes all i get is a command line.  this is what it says: ```
[   0.000000] ACPI: no dmi bios year, acpi=force is required to enable acpi
Loading, please wait
Linux ubuntu 2.6.27-7-generic #1 SMP WED OCT 22 00:29:18 UTC

The programs included with the ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with absolutely no warranty, to the extent permitted by applicable law.

To access official ubuntu documentation........

ubuntu@ubuntu:~$

```

This has happened with ubuntu 8.10 and now xbuntu 8.10.  I had ubuntu 8.04 installed on this computer previously and had no problem.

---

### Post by macogw on 2008-10-31
Are you able to just upgrade from 8.04?

---

### Post by rm2011 on 2008-10-31
Thanks for the quick reply.  No, I tried to just upgrade, but it didnt work.  And then I read that xubuntu would be better for an older computer because it uses less memory.  So i have tried both, and get the same result, which is none

---

### Post by rm2011 on 2008-10-31
When I try to boot off of the hard drive, the same thing happens.  I no longer get a login screen or anything, so i cant try just upgrading again.

---

### Post by reg4c on 2008-10-31
Perhaps try

```
start-x
```
someone correct me if this command is not right.

Also, try checking the CD for errors.
Cheers

---

### Post by angryfirelord on 2008-10-31
> **reg4c said:**
> Perhaps try

```
start-x
```
someone correct me if this command is not right.

Also, try checking the CD for errors.
Cheers
The command would be **startx**, not start-x. Also, try doing what the output says and boot up the LiveCD with acpi=force as a parameter to grub.

---

### Post by the.phantom on 2008-10-31
> 
I am trying to install xubuntu on an older laptop

what processor and how much memory on the old computer?

---

### Post by rm2011 on 2008-10-31
processor is a pentium II.  not sure on the memory.  how could i find this out?

---

### Post by kagashe on 2008-10-31
Type:
> free -mat the $ prompt.

---

### Post by rm2011 on 2008-10-31
ok this is what i get for the memory:  total-154  used-144 free-10  shared-0  buffers-4  cached- 118      swap: total-154  used 0  free-227

---

### Post by the.phantom on 2008-10-31
> ok this is what i get for the memory: total-154 used-144 free-10 shared-0 buffers-4 cached- 118 swap: total-154 used 0 free-227


I AM NOT A EXPERT !

but what i was thinking when i asked for processor and memory was to see what you have

and if you look at the min specks for Ubuntu i think you are light?

IF i am right maybe try a different flavor of unix?
maybe puppy linux or something?

i do have ubuntu 8.04 running on a p2 4oo mhx but with 384 of memory and it is sloooow. i can use it as a test box but it needs more memory to work right

on the different flavors of ubuntu they do list the specks of it and you can fudge some but you are fudging a bunch 

just my idea

---

### Post by rm2011 on 2008-11-01
Ok, I have tried to do the command: ```
startx
```
with no luck.  I get this messgae: ```
FATAL ERROR: NO SCREENS FOUND
GIVING UP
```

I dont have any idea what this means.  any ideas?  And also how would i do what was previously suggested with the ```
ACPI=FORCE
``` output?

---

