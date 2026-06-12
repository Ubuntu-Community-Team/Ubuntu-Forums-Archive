---
title: "Passphrase on every boot and unable to enable hibernate"
date: 2016-11-27
forum: New to Ubuntu
---

### Post by caterhamfan on 2016-11-27
Hey, Newbie to Ubuntu here. Two problems
 
I installed Ubuntu using USB.
 
 First, I partitioned my hard drive using gparted (livecd boot) because I stupidly installed without partitioning. My drive was encrypted and now every time I boot into Ubuntu it asks for a passphrase or none (pressing enter twice clears me to the login page). What did I do wrong? What can I do to fix this?
 
 
 Second, I’ve gone through numerous steps to enable hibernate including these:
 
 
 Still with no luck. My linux-swap is 20Gb and my RAM is 8Gb so that isn’t the problem. What could the issue be here? I really would like to use this feature for when I’m doing my university work.
 
 
 Grateful for your assistance folks :)

 
 
 Matt

---

### Post by Geoffrey_Arndt on 2016-11-27
Well, could it be that you did the install using a process called: . . . . . . "shooting from the hip"???

And the install process does not just enable encryption unless the user checks a box which then installs whole-disk encryption.   Not recommended at all for newbies.

Suggest you just whip in that USB and use gparted again to setup the right partitions and swap.   You for sure don't want 20 Gig . . . either 4 or 6 Gig is plenty, or 8 Gig maximum.

After install your system will utilize short suspend, and long suspend by default.   I "believe" I read that hibernation on Ubuntu was removed as an option 3 or 4 years ago - - but don't take that as Gospel.   But suspend will nearly shut down the system and pressing the start button "briefly" will bring you out of suspend.

Good luck!

---

### Post by caterhamfan on 2016-12-08
Thank you for your reply, 
I reinstalled Ubuntu and the problem is solved. 

I can't enable suspend via the kernel method at all. It just won't work. This is one feature Ubuntu really needs as default in my opinion. Still prefer it over MS though :)

---

### Post by ian-weisser on 2016-12-08
Suspend or Hibernate? Big difference.
Suspend already works by default on most hardware. Hibernate works on some hardware.

Ubuntu automatically tests your hardware for suspend and hibernate functionality - it your hardware fails, then Ubuntu won't offer the option.
New kernel developers to add the functionality to more hardware are always welcome.
Or you could purchase hardware from manufacturers that wisely enable that functionality for Linux by contributing to the kernel.

---

### Post by caterhamfan on 2016-12-09
Opps, I mean hibernate. It doesn't work the hardware I have I guess. No matter.

Thank you,

---

