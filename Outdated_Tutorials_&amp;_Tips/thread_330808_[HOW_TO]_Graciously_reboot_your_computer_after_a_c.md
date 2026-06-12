---
title: "[HOW TO] Graciously reboot your computer after a crash withouth unplugging"
date: 2007-01-03
forum: Outdated Tutorials &amp; Tips
---

### Post by raul_ on 2007-01-03
_Note:_
I've searched the forums but i couldn't find nothing regarding this subject, or at least any How-to's so here it goes

**In the event of a total system freeze up, this is the failsafe way to safely reboot a near-frozen computer. It should be noted that this is a Linux specific feature with potential security issues, so be certain to read about the implications before enabling this on production servers, and that for OS' other than Linux, they probably will respond differently to the SysRq key.**

So i think many here have faced this problem: You're working/playing with your Ubuntu, and all of a sudden, the system stops responding (Yes, crashes happen in this world too). And then you panic: "Oh no! Now i have to do a hard reboot and i'll have to go through:

1. 30 minutes of fsck if you're using ext2

2. May experience data loss if you're using ext3 (worse if you're using writeback journaling like me :mrgreen:)

So, the thing to do when not even ctrl+alt+backspace, nor ctrl+F1....F6 work is to press alt+sysrq+ the following combination, with some time between the strokes:

 R takes the keyboard out of raw mode
 S synchronizes the disk
 E terminates all processes
 I kills all processes
 U remounts all filesystems read-only
 B reboots the machine

hard to remember? try this:

**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**oring

**RSEIUB**

It really works ;) it's much safer than unplugging your computer. But remember, ONLY DO THIS IF NOTHING ELSE WORKS!!

---

### Post by userundefine on 2007-01-03
Guess the search feature isn't the best at finding [everything]("http://www.ubuntuforums.org/showthread.php?t=315404&highlight=all+else+fails").

But it's good information all the same and worth repeating. ;)

---

### Post by raul_ on 2007-01-03
Yes it seems it is :D Maybe some mod can merge the threads. Sometimes it's all about the (wrong) tags

---

