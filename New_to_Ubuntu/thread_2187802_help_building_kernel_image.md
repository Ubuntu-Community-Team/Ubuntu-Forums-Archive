---
title: "help building kernel image"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by squakie on 2013-11-13
I have been trying in my limited ability to help a user (see [this thread]("http://ubuntuforums.org/showthread.php?t=2186866")) with their question on getting their wireless working.  Another user posted back some instructions that required download kernel 3.12 source, building it, and booting from it.  The user has had problems since trying that.

I tried those same instructions myself to see if I could figure anything out, even though I don't have the OP's hardware.  In the building of the kernel, a LOT of questions are asked that require a n/y or n/m/y response.  I have no clue what the functions are that it wants answers on - and the OP just picked an answer (and now has no video).  After just guessing at a few myself, I just aborted the process and decided to ask for help on these options and/or help in the OP's thread.  I'm sure these are asking if you want "x" support built into the kernel (n/y) or as a loadable module (n/m/y) (I'm guessing), but without any ideas on what they are it just seems like an excersize in really trying to mess things up.

If anyone could be any help with this it would be greatly appreciated by the OP.  I'm WAY beyond anything I know here.

ADMINS:  I suppose this belongs in another place, but I couldn't see where.  I thought about development, but that appears to be a forum for application development, not questions on building a kernel.

---

### Post by Doug S on 2013-11-14
I never know how I should set all of the config options either, so I cheat. First, I would install the Ubuntu 3.12 kernel from the [kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). Then I copy the config file from /boot to my kernel build location, thus setting most if not all of the config options. The last time I did this, was 3.11RC2```
cp /boot/config-3.11.0-031100rc2-generic .config
```

---

### Post by squakie on 2013-11-14
That's EXACTLY what I needed to know!!!  It is also 3.13 kernel he was told to install, so this REALLY helps!!

Thank you!!

---

### Post by DuckHook on 2013-11-14
Don't mean to rain on the parade, but instructing newbies to compile their own kernels creates a "solution" that's worse than the problem. I've been tinkering with Linux since, what?... '96? '97? I only started compiling my first kernel three years ago with a Gentoo VM and only got the real hang of it late last year. For a newbie to attempt this would be like asking a 12-year-old to fly a jet plane. Is there no other solution to his/her problem? If the problem is a WIFI card, why not just disable it and buy a $15 USB WIFI stick that's known to work out-of-the-box?

---

### Post by Zill on 2013-11-14
> **DuckHook said:**
> Don't mean to rain on the parade, but instructing newbies to compile their own kernels creates a "solution" that's worse than the problem...
**+1**
I have been using Linux systems for over ten years now and have never felt the need to compile a kernel.  I might try it one day though when I have gained more experience... ;-)
> **DuckHook said:**
> If the problem is a WIFI card, why not just disable it and buy a $15 USB WIFI stick that's known to work out-of-the-box?
An excellent solution and no kernel tinkering required. :-)

---

### Post by Doug S on 2013-11-14
> **squakie said:**
> It is also 3.13 kernel he was told to install, so this REALLY helpsThere is no 3.13 kernel yet.

As to the points made the others compile verses do not compile: I was just answering the question.

---

### Post by squakie on 2013-11-14
It was a different user who recommended building the 3.12 kernel to the OP.  That user has now provided links to binaries so the user doesn't have to build.  I haven't said anything else there, except to pass along the info on using existing options as mentioned above.  However, I'm leary of any binary that doesn't come from the repositories.  I would prefer the user follow the thread I posted a link to - I believe it was in launchpad - again but this time tell us the error message and we can go from there.  All it's doing there is building the wireless driver, not the kernel.

BUT.......I'm am WAY out of my environment with this in linux - old proprietary OS's  not a problem - but haven't even bothered to look at any of this for linux.

SO.....If one of you more knowledgable people could go to the OP''s thread (I think I put a link to it in my initial post) and perhaps help the user it would be greatly appreciated.  The OP is just starting with linux, and it seems the other user sort of pushed them off the deep end of the pool, instead of starting in the kiddie pool.  If they follow just building the wireless driver I can probably help, but all of this other stuff about building a new kernel or downloading a binary image to use is first and foremost beyond my comfort and knowledge zone, and second I consider it dangerous to download an "unknown" binary.

Thanks for any help you might be to the OP in the post I linked to.  This is all just for helping them.

---

### Post by squakie on 2013-11-14
> **Doug S said:**
> There is no 3.13 kernel yet.

As to the points made the others compile verses do not compile: I was just answering the question.

Sorry - fat fingered that - it is 3.12.

---

### Post by squakie on 2013-11-14
> **DuckHook said:**
> Don't mean to rain on the parade, but instructing newbies to compile their own kernels creates a "solution" that's worse than the problem. I've been tinkering with Linux since, what?... '96? '97? I only started compiling my first kernel three years ago with a Gentoo VM and only got the real hang of it late last year. For a newbie to attempt this would be like asking a 12-year-old to fly a jet plane. Is there no other solution to his/her problem? If the problem is a WIFI card, why not just disable it and buy a $15 USB WIFI stick that's known to work out-of-the-box?

A different user has recommended building the kernel.  The original link I posted in the OP's thread is to a launchpad thread on just building the driver.

As far a a different wireless adapter, that would need to be mentioned to that OP.  I personally have been using a certain Tenda USB wireless N adapter and have yet to have any problems - it just works, and it always connects at 300mps.  Our local Micro Center had them marked down (last week anyway) from $29.99 to $12.99, so I picked up a couple of spares.  They have also worked fine in any Raspberry Pi I have used - Raspbian, Openelec, etc., with no problems or set up.

---

### Post by squakie on 2013-11-15
Well, the OP in the other post downloaded the binaries from the other user and at least fixed their wireless issue.  So, for me at least, I don't need this thread anymore.  I've gotten in trouble in the past for marking a thread "solved" if there is no solution in the thread that worked for me, so I can't mark this solved, just dead.

---

