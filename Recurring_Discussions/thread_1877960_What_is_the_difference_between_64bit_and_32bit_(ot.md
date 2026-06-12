---
title: "What is the difference between 64bit and 32bit? (other than size)"
date: 2011-11-09
forum: Recurring Discussions
---

### Post by JoshuaMiller0 on 2011-11-09
What is the difference between 64bit and 32bit? (other than size) is one faster? more powerful? Need a better comp?

---

### Post by dcstar on 2011-11-09
> **JoshuaMiller0 said:**
> What is the difference between 64bit and 32bit? (other than size) is one faster? more powerful? Need a better comp?

64-bit software fully utilises the capabilities of 64-bit hardware, 32-bit does not.

---

### Post by Fred Doolie on 2011-11-09
> **JoshuaMiller0 said:**
> What is the difference between 64bit and 32bit? (other than size) is one faster? more powerful? Need a better comp?

Unless I'm mistaken a 32bit OS can only handle 4Gigs of RAM (more like 3.8 or something like that). You need a 64bit OS if you have more than 4 Gigs or RAM.

I've heard though that 64bit OSes have lots of problems with 32bit software. You need special 64bit versions of stuff. I think!

---

### Post by HellesAngel on 2011-11-09
Not strictly true, either of those points.  Here's a nice site that explains the 3 gigabyte limit myth rather nicely, as usual is springs from the Windows world and [Microsoft's half-truth marketing]("http://www.geoffchappell.com/viewer.htm?doc=notes/windows/license/memory.htm").  

As to the problems with mixing software - 64 bit Windows generally has no problems with 32 bit software and the various Linux flavours can mostly be made to play along in the same way, providing both sets of libraries are available.  A 32 bit machine cannot run 64 bit software, however.

---

### Post by tartalo on 2011-11-09
64bits is slightly faster (unnoticeable in a common PC)

---

### Post by Elfy on 2011-11-09
Thread moved to Recurring Discussions.

---

### Post by Fred Doolie on 2011-11-09
I stand corrected.


> **HellesAngel said:**
> Not strictly true, either of those points.  Here's a nice site that explains the 3 gigabyte limit myth rather nicely, as usual is springs from the Windows world and 

Leave it to M$ those........*mumble mumble* guys.

But..System Monitor in Ubuntu shows me as having only 2.7 Gigs of RAM. I have 4 gigs installed! It also shows only one CPU. I have a dual-core. Something is goofy here. Is that because I'm not using a PAE kernal? The PAE kernal in 11.10 wont boot for me. It locks up.

---

### Post by HellesAngel on 2011-11-09
There can be various things stealing or hiding your installed memory - the BIOS can be remapping it for onboard graphics or IO, or perhaps something weird.  If you have a 64 bit kernel installed on a 64 bit machine then you do not need PAE, if you have 32 bit then you may do.

---

### Post by Fred Doolie on 2011-11-09
> **HellesAngel said:**
> There can be various things stealing or hiding your installed memory - the BIOS can be remapping it for onboard graphics or IO, or perhaps something weird.  If you have a 64 bit kernel installed on a 64 bit machine then you do not need PAE, if you have 32 bit then you may do.

Oh I see. That 2.7 is "available for system" use rather than "total physical RAM installed"  Ok ty Time to dig into the BIOS and see where its being used. .5 Gig of the "missing memory" is graphic card then.

---

### Post by dpny on 2011-11-09
> **HellesAngel said:**
> Not strictly true, either of those points.  Here's a nice site that explains the 3 gigabyte limit myth rather nicely, as usual is springs from the Windows world and [Microsoft's half-truth marketing]("http://www.geoffchappell.com/viewer.htm?doc=notes/windows/license/memory.htm").  

Correct me if I'm wrong, but the article seems to say that you can hack 32-bit Windows so it can see more than 4 GB. But I didn't see any mention of the ability to get a thread/application to access more than 4 GB, which is the real point of 64-bit.

---

### Post by cariboo on 2011-11-09
> **dpny said:**
> Correct me if I'm wrong, but the article seems to say that you can hack 32-bit Windows so it can see more than 4 GB. But I didn't see any mention of the ability to get a thread/application to access more than 4 GB, which is the real point of 64-bit.

The [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") kernel allows you to access up to 64GiB of ram on an i386 platform. There is a pae enabled kernel in the repositories.

---

### Post by dpny on 2011-11-09
> **cariboo907 said:**
> The [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") kernel allows you to access up to 64GiB of ram on an i386 platform. There is a pae enabled kernel in the repositories.

I understand. But the article didn't make it clear to me whether that means only the OS can see the extra memory, or if the the apps can also make use it. The real reason for going 64-bit is not that the kernel can address more than 4 GB, but that apps which move around large amounts of data can access more than 4 GB. If the OS can access 4+ GB, but an app running in that OS can not, then it's not really useful. In all practicality you're still stuck with the 4 GB limit.

---

