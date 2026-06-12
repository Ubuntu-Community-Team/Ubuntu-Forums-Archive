---
title: "Black bar on left of acer monitor after upgrading to 8.04"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by tiakitty8 on 2008-09-04
Hello!

I'm not new to Ubuntu (used about a year) but I'm a novice in using the terminal, troubleshooting, etc. 

When I upgraded my Ubuntu 7.1 to 8.04, my 20" acer monitor had a 2" black bar along the left-hand side. It was like the centerline of the desktop shifted 2" to the right. The date/clock and Log off switch, etc. was off screen. 

The screen was perfect with Ubuntu 7.04 and the upgrade to 7.1.

I checked my screen resolution (Systems--Preferences--Screen Resolution)
and it was 1280x1024 @ 75 Hz: correct for my monitor. Using Screens and Graphics, it recognized it as an acer 20" monitor and identified my VGA as i810 Intel Integrated Graphics Chipset. In other words, to this noob my os correctly identified my monitor, it just didn't set the desktop up right.
 
I tried manually adjusting my monitor via the menu but could only shift the desktop over about 3/8" to the left.

I searched on Google and these forums for hours but couldn't find anything like my problem. In desperation, I reinstalled Ubuntu 7.04 from a LiveCD, did all the updates through 7.1 and upgraded to 8.04 in case the upgrade was corrupt somehow. Same bad result.
 
I installed Kubuntu 7.1: same problem with the black bar on the left side of the monitor. Ditto with Edubuntu 7.1. I downloaded an .iso of Ubuntu 8.04 and Kubuntu 8.04 still thinking my upgrades may have been corrupted somehow. 

With clean installs of both Ubuntu 8.04 and Kubuntu 8.04, the exact same issue! I downloaded an .iso of Mint 4 as an experiment and installed that: same monitor problem. 

I had to reinstall Ubuntu 7.04 and upgrade to 7.1 and just stay there for now to have a complete desktop. Is this a bug not yet reported? Or is this a simple fix that due to my inexperience I'm just spinning my wheels?

I would really love to know how to fix this so I can upgrade. I've spent about thirty hours uninstalling, reinstalling, searching, and banging my head against the wall on this. I hope one of you kind-hearted Ubuntu gurus out there can save this noob from the pain of my ignorance!

Thank you all in advance for your time. Sorry for the long post: I didn't know how to shorten it up and still explain the issue correctly.

---

### Post by mike555 on 2008-09-05
If you are using a lcd monitor your setting should be 60 hz ..........

---

### Post by tiakitty8 on 2008-09-05
Hello Mike555! Thank you very much for your reply.

I do agree with you: I felt my monitor should've been set to 60Hz (my last one was). The owner's manual for my monitor specified that the monitor should be set to 75Hz and to adjust the VGA, if needed, to reflect this.

At 75Hz the acer monitor works perfect with Ubuntu 7.1 (upgraded from 7.04 per my post above). You feel if I adjust to 60Hz with a 8.04 upgrade this will solve my off-centered desktop? I could try this (heck, I'm open to anything at this point) but I thought the frequency rate was for "refresh" (i.e. minimizes flicker,etc.). Would this difference in refresh rate create the black bar on the left hand side? If so, why is my desktop/screen perfectly centered using 7.1 at 75Hz?

Forgive my questions. I'm just trying to wrap my head around this problem and am confused with what the refresh rate has to do with the black-bar along the left of my monitor.

Thank you again for your time answering my post.

---

### Post by mike555 on 2008-09-05
I'm not sure , but I've always been told that running a LCD monitor higher then 60 would hurt it ..... but then , new monitors might be different ...

---

### Post by mike555 on 2008-09-05
You didn't say what graphics card you have, you might need new drivers ......




 my mistake , you did say integrated, still you might check for drivers in the package manager, just search for i810 ....

---

### Post by tiakitty8 on 2008-09-05
Thank you again mike555 for the suggestion. Why didn't I think of that? I've got the noob blues rattling in the brain pan, I guess. I will try that out, too.

I have done some more exhaustive searching and ran across a bug with 7.1 and 8.04 in regards to widescreen monitors like mine. Some posts for help in other forums have describe the identical problem, each with varying degrees of success. 

They talk about manipulating something in an "xconfig" file or something like that (not looking at it right now so I can't quote exactly). I do know I never heard of that and am confused following the post's responses clearly written by experts for experts. Maybe a solution is there but I wouldn't know it if I fell right into it. <sigh>

I need to run off to work now, but I'll check back later.

Again, thank you for your time and suggestions. When I learn more I'll let you know and definately "pass it on"!

---

### Post by rahulkucheria on 2009-02-26
hi friends i have windows 7 os beta 7000 and its working perfectly but i got a cd of ubuntu 8.10 and i rebooted my system with the cd and just wanted to see how it works so i selected use without installation and i used it and got a black bar to the left and some of the contents on the right side like the close button disappeared so what should i do please help me.

---

### Post by thomps on 2009-02-26
Hi tiakitty8,

This is just a thought, but I know when I install my restricted NVIDIA driver, there is an "AUTO" setting on my monitor that automatically adjusts screen position, etc.  Maybe give that a try before changing settings in Ubuntu.

thomps

---

