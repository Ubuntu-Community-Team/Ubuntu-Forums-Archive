---
title: "Space available?"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by d4m1r on 2013-01-24
Hi, although I don't consider my self an absolute beginner, I feel like this question belongs here :) Basically, if you go to System Monitor > File Systems, and you look at your EXT4 Ubuntu partition, something looks wrong to me....

[IMG]http://i.imgur.com/9dQaX9Ll.png[/IMG]


Why is "Free Space"  11.3GB but "Available Space" is 10.3GB? If I right click on my partition under Ubuntu or even under Windows, both also show 11.3GB left of free space....That makes sense as my total EXT4 partition is 19.2GB in size and 7.9GB of that is used. Anyone know where Ubuntu gets that number from? I should also mention I do not have a swap partition....

---

### Post by elgordodude on 2013-01-24
One of the vagaries of ext, 5% of the partition is reserved for root. Not generally a big deal and probably too much nowadays, but if your disk is at 95% a new disk should be a priority anyway

---

### Post by d4m1r on 2013-01-24
> **elgordodude said:**
> One of the vagaries of ext, 5% of the partition is reserved for root. Not generally a big deal and probably too much nowadays, but if your disk is at 95% a new disk should be a priority anyway

1) If 5% of the partition is solely for the root user, how is 10.3GB 5% of anything?

2) So wait guys, which do you believe do the actual amount of free **usable** disk space, 10.3GB or 11.3GB?

---

### Post by elgordodude on 2013-01-24
Well 10.3 is 5% of 200 GiB, but that's a happy coincidence, the 5% is the missing 1 GB of 19.2 GB between free and available.

You *can* overwrite root if need be, but I'd say the *usable* space is 10.3

edit: Actually I'd say the *usable* space is a little over 7 GB. It's bad luck to push a drive past 90%

---

### Post by audiomick on 2013-01-24
> **elgordodude said:**
>  5% of the partition is reserved for root.

> **d4m1r said:**
> 1) If 5% of the partition is solely for the root user, how is 10.3GB 5% of anything?

I think you are mixing up "root user" and root. Bear in mind that the system has a user called root that is not you.  It is the system running itself, and it is this function that is making 5% of your space not available to you, the user who is logged on.

I believe this still applies even if you are logged on as root, which you are not on a standard Ubuntu install. On a standard Ubuntu install, you, the user, can gain root priviliges using the sudo mechanism, but you are not root.

---

### Post by prodigy_ on 2013-01-24
> **d4m1r said:**
> how is 10.3GB 5% of anything?
19.2 - (0.96 + 7.9) = 10.34 where 0.96 is 5% of the total size (19.2GB).

---

### Post by d4m1r on 2013-01-24
> **prodigy_ said:**
> 19.2 - (0.96 + 7.9) = 10.34 where 0.96 is 5% of the total size (19.2GB).

Oh, that makes sense now, thanks.

So that 5% **is **dedicated to the root user, but is it still considered "usable"? Ie: do I actually have 10.3GB of free space or 11.3GB of free space for my files?

---

### Post by mcduck on 2013-01-24
> **d4m1r said:**
> Oh, that makes sense now, thanks.

So that 5% **is **dedicated to the root user, but is it still considered "usable"? Ie: do I actually have 10.3GB of free space or 11.3GB of free space for my files?

it's usable, but not by your normal user. You can use the last 5% if you do it as root. (But you probably shouldn't, even though Ext filesystems are very resilient against fragmentation, it will become an issue and quickly decreases the performance if the drive is too full. So unless you absolutely have to, you wouldn't want to fill the drive up to 100% anyway)

---

### Post by MadmanRB on 2013-01-24
There is also file allocation involved too and how it works with said operating/file system.
Each one treats file space a little differently and can get confusing if you dont know how a file system is supposed to work.
There is indexing to consider too, and reserved space too, both linux and windows work like this in the end.

---

### Post by d4m1r on 2013-01-24
> **mcduck said:**
> it's usable, but not by your normal user. You can use the last 5% if you do it as root. (But you probably shouldn't, even though Ext filesystems are very resilient against fragmentation, it will become an issue and quickly decreases the performance if the drive is too full. So unless you absolutely have to, you wouldn't want to fill the drive up to 100% anyway)

Exactly what I was looking for, thanks!

---

