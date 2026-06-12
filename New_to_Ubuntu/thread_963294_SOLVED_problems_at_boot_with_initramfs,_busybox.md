---
title: "SOLVED: problems at boot with initramfs, busybox"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by ginestre on 2008-10-30
PROBLEM: With Feisty, Gutsy and Hardy (and maybe others), boot hangs intermittently at the busybox with an interminable initramfs error.

SOLUTION: Boot with the IRQPOLL option.

JUSTIFICATION FOR POSTING:

I have spent months on this, and found all sorts of stuff scattered throughout this forum and other places with lots of helpful ideas, none of which unfortunately worked for me. So when yesterday I finally got the damn machine going I thought it useful to put this post here with the (simple) solution clearly in evidence, just in case others are suffering as I did. 

In my case, the problem seems to have been faulty firmware on the disk controller (it's a JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02) ) which just doesn't do its stuff under Ubuntu for some reason, though it works fine in XP. 

If I understand the function of IRQPOLL properly -don't take that for granted I'm just another newbie- this option will force the boot to examine IRQ needs one by one, and try to find a solution. If that's what it does, it may well be the answer to similar problems, and is easy to try!

---

### Post by Dumpy Dumpster on 2008-11-03
Good Morning ginestre.   I did see your post earlier during my searches, but could you tell me how to 'Boot with the IRQPOLL option'.  I was going to try to e-mail you later today if I got no further responses!   Thanks

---

