---
title: "Problems with GMA 3150 Graphics"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by bracus on 2012-03-26
I've been searching like crazy trying to find a fix for this, it's the only thing that's not completely working on my setup.  I have a Gateway LT2802u netbook and I installed 11.10 on this 2 days ago.  Everything works except for accelerated graphics.  At first I couldn't watch a simple flash video at all, but somehow I got it to work.  Now the last problem I have is I can't watch HD videos, my screen resolution won't go higher than 1024x600, and my under my graphics driver it says "Unknown".  

After doing as much research as possible, I've come to the conclusion that it's the GMA 3150 graphics driver.  There is a bunch of talk on it all over the interwebs but nothing lately.  I've tried the fixes that some people have used but most when I try to get the package it's no longer there or available if that makes sense.  I'm loving everything Ubuntu has to offer but it'll really bite if I can't use it any more because of this problem.  Does anybody have any ideas?  You'd really be helping a lot.

Also, not sure if this will help but this is the info I pull up on it.

```
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 058f
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 56180000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 40a0 [size=8]
    Memory at 40000000 (32-bit, prefetchable) [size=256M]
    Memory at 56000000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```

---

### Post by Perfect Storm on 2012-03-26
Have you tried adding x-swat PPA to your sourcelist?
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
to get a newer driver?

---

### Post by bracus on 2012-03-26
Yeah I added it.  Although, for some reason during the install it does have some errors but still completes.

---

### Post by Perfect Storm on 2012-03-26
Can you post the errors?

Also try the testing PPA of x-swat (use it on your own risk);
[https://launchpad.net/~ubuntu-x-swat/+archive/ppa](https://launchpad.net/~ubuntu-x-swat/+archive/ppa)

---

### Post by bracus on 2012-03-26
Sorry for the delay, long day at work.  I may be wrong, maybe they aren't related to that specific package.  But maybe you'd know if it's directly related to the problem.  Here's what I get when I update:

```
W: Failed to fetch http://ppa.launchpad.net/alex-p/notesalexp/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/alex-p/notesalexp/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gma500/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gma500/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by bracus on 2012-03-26
Ok after doing some more work, I finally got it to change from "Unknown" to "Intel® IGD x86/MMX/SSE2 ".  HD video still doesn't play though.  Are there any settings I can adjust to do so or am I just out of luck?

---

### Post by mikewhatever on 2012-03-26
It might be obvious, but GMA500 and GMA3150 are not the same. You should remove the gma500 repository as well as the other one that spits out errors.

That settled, let's deal with GMA3150. While that "accelerated" slug works relatively well with Linux, playing HD videos, especially flash videos, is out of the question. You might be able to play a downloaded p720 video in mplayer with tolerable amount of stuttering, but not more then that.

Intel's "accelerated" graphics is one reason OEMs stopped selling netbooks.

---

