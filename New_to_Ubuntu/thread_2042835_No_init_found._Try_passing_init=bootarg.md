---
title: "No init found. Try passing init=bootarg"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by tezarin on 2012-08-15
Hi all,
 
My server cannot boot anymore and I keep getting this error messages:
 
```
No init found. Try passing init=bootarg
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

```
 
The output of uname -a is: 
```
Linux (none 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 unknown
```
 
I burned a live Ubuntu CD. The file I burned was ubuntu-12.04-desktop-i386.iso
Then I booted from this live CD and clicked on "Try Ubuntu". 
 
Next, I opened a terminal and typed ```
fsck -y /dev/sda1
```
 
It showed me an output with the word Clean in it. Nothing further, so I thought that must have fixed the issue so I booted from the hard drive and back was back to square one, got the very same error message as above.
 
Would someone please help me fix this issue? Maybe I needed a different version of the Ubuntu live CD, I would really apprediate any help.

---

### Post by s1baker on 2012-08-15
I think this type of problem may be spreading. Same thing happened to me yesterday.
Someone else had similar problem earlier.
Check out reply #5

[http://ubuntuforums.org/showthread.php?p=12174320&posted=1#post12174320]("http://ubuntuforums.org/showthread.php?p=12174320&posted=1#post12174320")

---

### Post by tezarin on 2012-08-16
> **s1baker said:**
> I think this type of problem may be spreading. Same thing happened to me yesterday.
Someone else had similar problem earlier.
Check out reply #5
 
[http://ubuntuforums.org/showthread.php?p=12174320&posted=1#post12174320](http://ubuntuforums.org/showthread.php?p=12174320&posted=1#post12174320)
 
 
Thanks for your reply. My machine doesn't show a black screen, it also shows that message I posted in my first post...Do you think gparted will be able to fix that, too?

---

