---
title: "Fixing a system freeze"
date: 2005-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by trico on 2005-04-28
I've had a long history of freezes with Ubuntu.  The freeze would usually occur after the system was left on overnight.  When I would try to do something with it the next day it would would perform verrrry slooowwwllly.  Shutting down would happen eventually, but it would take at least 20 minutes, perhaps longer.

My system has the 2.4 ghz hyper-threading cpu.  It made no difference if I was using an SMP kernel or not.  Or if I had hyper threading enabled in the bios or not.    I thought it had something to do with the drivers Ubuntu was using but was wrong.  I loaded another distribution onto the system and had the same problem. 

I went looking for a BIOS update and found that IBM had posted a new one a while back and in the list of things it fixes, there is a mention of possible problems with some Intel CPUs and a new microcode load for the CPU to fix it.  

To cut a very long story short - the problem was with the bios/intel cpu.  I downloaded the Bios, installed it and have had no problem since.    I've re-enabled hyperthreading in the bios and am now happily using the SMP kernel.  No more system freezes.

trico

PS: I'm sure there's a better place for this post but after reading through the descriptions of the various fora I haven't a clue where it belongs.  I don't seem to be able to post to the message threads where I first described the problem.  So I'll leave it to the powers that be in ubuntu-land to move this to wherever it belongs.

PPS: I have XP on the same system and it appears to not be sensitive to the problem.    Interesting...

---

### Post by vnbuddy2002 on 2005-04-28
I had the same issue with the same CPU specs. It froze after 24 hrs and it caused by Xorg that consumed 99% of the CPU. After I upgraded to kernel I686, the problem is gone. I am happy that my linux box is still non-crash for nearly two weeks.

:)

---

### Post by trico on 2005-04-29
I logged in while the system was failing and using 'top' was unable to see anything bad going on with Xorg.  In fact, SSH, accessed from windows (Putty) was performing irratically too.  When top showed something it did not show any large consumers of the cpu.  

I can't prove it, but it's my opinion that it was a cpu problem that Intel has since found a work-around for.  It may be that the cpus in question only went to certain vendors and IBM, where I got my system, was one of them.

trico

---

