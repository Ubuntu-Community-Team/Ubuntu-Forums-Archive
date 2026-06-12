---
title: "Booting Heron with NeoGrub"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by olivergringold on 2008-07-04
Howdy.  I'm trying to use NeoGrub to boot into Hardy Heron, but, as you might guess by my admission of being an absolute beginner, things aren't going quite as planned.

However, I do think I might have the savvy to know what the problem *is*...I merely need help fixing it.

Here reads the NeoGrub boot information for Hardy:

"#This is the only entry
title		Booting Ubuntu Linux (Skip Notification: "Enter")... 
root		(hd0,1)   	#Load Ubuntu from the 1st hard disk's 2nd partition.
#Next Line: Translate (hd0,1) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdbc
initrd		/boot/initrd.img-2.6.22-14-generic
#End Ubuntu entry"

Here's the deal...I'm going to guess, right off the top of my head, that the kernel and initrd locations are dead wrong.  This guess stems from the fact that I get "Error 17: File not found" every time NeoGrub tries to load the kernel.  "If you know this," you might scoff, "then what's the problem?"

Well, I, being an idiot, have no idea *whatsoever* as to the *correct* locations, and therefore am presently in a deadlock with my computer.

As a point of interest, EasyBCD has had no troubles helping me boot XP or Vista...but I **really** want to take Hardy for a spin, and in that spirit hope somebody here will be able to help me.

Whaddaya say?

-Olly

---

### Post by jeffimperial on 2008-07-04
Well, I'm no expert too but here's what I know:

Each physical volume is named sda, sdb, sdc... with the sda as first primary master, second one is primary slave and so on.

As for (hd#,#), these are volume-to-partition name conventions. If you have hd(0,1) that means the first hard disk, the second partition. (note that counting starts from **zero**)

---

### Post by caljohnsmith on 2008-07-05
> **olivergringold said:**
> 
"#This is the only entry
title		Booting Ubuntu Linux (Skip Notification: "Enter")... 
root		(hd0,1)   	#Load Ubuntu from the 1st hard disk's 2nd partition.
#Next Line: Translate (hd0,1) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdbc
initrd		/boot/initrd.img-2.6.22-14-generic
#End Ubuntu entry"

For one thing, it appears you have the "root=/dev/sdbc" set incorrectly. Since you are using (hd0,1), it should be "root=/dev/sdab" I believe. I'm assuming that your kernel and initrd locations are probably correct, but if changing to the "root=/dev/sdab" doesn't solve the entire problem, we can go from there. :)

---

