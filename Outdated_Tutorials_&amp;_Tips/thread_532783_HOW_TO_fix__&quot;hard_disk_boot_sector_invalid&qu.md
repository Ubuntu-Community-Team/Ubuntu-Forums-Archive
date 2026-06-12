---
title: "HOW TO fix : &quot;hard disk boot sector invalid&quot;"
date: 2007-08-23
forum: Outdated Tutorials &amp; Tips
---

### Post by DiceMan on 2007-08-23
Are you trying to boot your computer only to get "hard disk boot sector invalid" and something about pressing H to retry? Well I got that and it took me a while to figure out the problem. The solution that's usually presented on the forum seems to be:
> sudo grub
root (<tab>
setup (hd0)That might help some people. In my case the problem was I'd removed the only bootable partition (formerly windows) and resized the linux partition to include that, but without setting a bootable flag (duh). To set a partition as bootable, simply boot using the Ubuntu live CD, choose "boot from hard drive" and when in ubuntu use any partitioning software to set your linux partition as bootable. GNOME partition editor is userfriendly - right click your ext3 partition, choose manage flags and add boot. 

Good luck!
//DM

---

### Post by Bob Todd on 2007-12-01
Is the second line correct? Terminal says error 23: Error while parsing number.

EDIT: I found out from another thread that <tab> means press the tab key, not type '<tab>'. How can I delete this post?

---

