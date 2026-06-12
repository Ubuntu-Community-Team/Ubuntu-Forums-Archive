---
title: "Driver Updates"
date: 2015-01-01
forum: New to Ubuntu
---

### Post by quintin4 on 2015-01-01
I just built my first pc ever. I followed up with wanting to get away from Microsoft so I decided to try Linux Ubuntu. I used an MSI mother board and am trying to figure out if its possible to update the drivers on my board and video card? When i go to the websites ubuntu comes up with an error. Any ideas or help would be appreciated. Dont make me go back to windows!

---

### Post by Bucky Ball on 2015-01-01
Welcome. The drivers for your board and graphics are part of Ubuntu, not resident on the board or graphics card. You can also install proprietary drivers for graphics if you need them. Open 'Additional Drivers' and see if it comes up with anything. You need to have the third-party (and possibly partners) repositories enabled in Software Sources (that may be called something else in Ubuntu). ;)

Are you having any problems with the install? Something not working?

---

### Post by Bashing-om on 2015-01-01
quintin4; Hi ! My Welcome to the forum in general

AND to 'buntu in particular.

Yeah as Bucky Ball says. Keep in mind this is not Windows, and we 'getter done' in a different manner.

The kernel, package manager, and software repository take care of 99% of anything and everything. This system has been around for a long time and in that time it has evolved and developed. If you need outside sourcing you will know it, 'cause the system will tell ya .

New hardware, developed for other markets takes a while for the linux world to adapt to .. driver wise and some obscure stuff can be difficult to handle.
For the most part - it just works.

When it don't work, we find out why
[INDENT][INDENT][INDENT][INDENT]that the 'buntu way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-01-01
+1 to Bashing-om's great explanation delivered in their usual unique style. ;)

---

### Post by buzzingrobot on 2015-01-02
> **quintin4 said:**
> ... trying to figure out if its possible to update the drivers on my board and video card? When i go to the websites ubuntu comes up with an error. 

Best thing to do is to post the exact error message you're seeing at those web sites. Plus the version of Ubuntu you're running, the video card brand and model, and the other hardware specs of your system. Especially if you've built yourself a cutting edge system.

If you aren't seeing a specific error message, try to describe what you do see, and if it's repeatable:  Can you trigger it by going to a specific site or by taking some specific action? 

Do you see these errors only using the browser, or elsewhere?

The Linux kernel is excellent at detecting hardware components and using the correct drivers, without requiring user intervention.  But, the very latest cutting edge hardware may occasionally be an issue, especially for components like video cards (vendors don't release source for the internals of their cards to the Linux commnity).

---

