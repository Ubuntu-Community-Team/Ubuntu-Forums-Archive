---
title: "solaris vs linux"
date: 2008-08-04
forum: Other OS Talk
---

### Post by xoger on 2008-08-04
what are the main differences between these two OSs. is there for instance a difference in speed, programs, 3d effects, support.

---

### Post by Dan_Dranath999 on 2008-08-04
I tried openSolaris 2 weeks ago. it looked just like a regular linux distro (but it recognized my wacom bamboo, with all The hassle i've had with it on Gutsy) i suppose the differences can't be seen by common users.

---

### Post by Anzan on 2008-08-04
That's right. All the userland aspects are the same except that the community is small and so is the number of software packages available.

But OpenSolaris has ZFS and other nifty featues useful to sys admins and such.

---

### Post by cardinals_fan on 2008-08-04
The Solaris kernel is completely different from the Linux kernel.  It's not just "Unix-like" - it IS Unix.

---

### Post by klange on 2008-08-04
I have a machine which refuses to do quite a few module-related tasks under Linux. Put simply, any Linux distribution under any kernel will fail (the core reason is a faulty / damaged mother board).

OpenSolaris? Runs perfectly.

Only problem I've had so far is that the installer doesn't resize NTFS partitions and drivers for a BCM4401 wired NIC must be compiled separately.

And userland is all I care about. If I can run Compiz and Mono, I can do what I need to do.

(Also have a Bamboo as my only mouse-type input, great that it detected it nicely. Love the fact that it comes with the nVidia drivers, too.)

For me on this machine, Solaris wins.

---

### Post by exploder on 2008-08-04
OpenSolaris is a very young project that shows real promise.Give OpenSolaris a little time and it will be very competitive.

---

### Post by stream303 on 2008-08-05
While hardware issues can be ironed out, the biggest issue seems to be that of governance:  are the users/devs in control, or is it ultimately the marketing department?

I for one wish them well and hope to see them truly join the open-source community, as long as it is sincere.

---

### Post by cardinals_fan on 2008-08-05
> **exploder said:**
> opensolaris is a very young project that shows real promise.give opensolaris a little time and it will be very competitive.
+1

---

### Post by dca on 2008-08-06
I'm holding out for the SCO/Novell/IBM dealie.  Novell owns UNIX (complete) and Sun licensed UNIX away from SCO which they couldn't legally do.  It's confusing but it seems Sun has a 'get out of jail free' card that they can pull if Novell decided to do anything weird.
 
As Sun's hardware (SPARC & others) sales goes down I see it harder for them to hang on to Solaris besides for providing existing client's support for Solaris 8,9,10.  It makes it look like this is the sole purpose for openSOLARIS is to get outside help.  Make other people do the work and Sun will get ultimate say as to what goes in.  This way what kernel devs are left at the company can concentrate on nothing but the kernel and outside contrib's will work on everything else whilst Sun employee's having final say of what is added to kernel.
 
Look at it from this angle, MS has over 20k paid devs working on their garbage (hence charging $400 for Vista). IBM has 250 paid programmers working on AIX.  Opening up the code makes better business sense.  IBM on the other hand went a different route (which cost them over $5b in donations) and got RHEL & SLES certified on most of their hardware platforms.  It's genius.

---

### Post by articpenguin on 2008-08-06
solaris has this awesome filesystem called ZFS. Too bad it cant get ported to linux because of the gpl.

---

### Post by dca on 2008-08-06
Oh, as far as Solaris versus Linux:
 
Solaris is UNIX at heart, more similar to HP-UX & AIX from IBM than BSD. Solaris uses containers similar to AIX LPARS versus actual VM.  Solaris uses ZFS which is far superior to ext3 and designed from the start to be used on mainframes or bigger iron.  It's not the license that separates it more than the paths the companies/developers taken with the kernel.  This would be why you'd never see Solaris installed on say a MID or cellphone.  Linux (kernel) is malleable, you can put it on anything.

---

### Post by jbrown96 on 2008-08-06
If you're only interested in userland, I would stick to Linux. I tried OpenSolaris and besides being disappointed with the number of applications available, it ran slow on my Core 2 Duo @ 2.0GHz. Solaris scales up very well to huge mainframes using SPARC processors, but doesn't scale down very well. It tends to run sluggish on reasonably current desktop hardware. Linux, on the other hand, scales down to embedded systems very well and has better performance on the desktop, although this greatly depends on the distro.

---

