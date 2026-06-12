---
title: "Hanging on install problem and question - how do I disable ACPI/splah screen"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by jeremyinrenton on 2013-02-24
Hello, 

I've been having nothing but problems attempting to install (from DVD) both Mythbuntu (which I gave up on) and Ubuntu 12.04.  

The machine already has an active Windows 7 partition but I'm trying to install Ubuntu to an entirely free partition on the same physical drive.

In both cases, the installation hangs during the 'Where are you' screen.

Some of the google search results I came up with advise disabling the ACPI option (under F6 boot options) as well as the splash screen.

How then, in the context of the CD/DVD installation flow/process does one disable the splash screen?

Ultimately I am trying to determine where and what the install is hanging up on.

Thanks in advance.  

-J

---

### Post by cortman on 2013-02-24
Hi jeremyinrenton,

First, props to you for sticking with it and doing some research! :)

[This thread]("http://ubuntuforums.org/showthread.php?t=950191") should help.

---

### Post by jeremyinrenton on 2013-02-24
Thanks cortman, I'll give that topic a thorough going-over.  

I'm still hoping that I can get Mythbuntu installed on this, my existing Win 7 media center PC, and maybe with luck get XBMC up and running on it as well.   

I've been running my own Debian Linux LAMP server for some years now so Linux isn't anything terribly unfamiliar to me.  And yet in a way I'm strangely sad about the fact that I getting stuck in the GUI install portion of trying to get this distro up and running.

---

### Post by jeremyinrenton on 2013-02-24
Well, I enabled, rather disabled, acpi=off, noacpi, and nolacpi and this time the installation of Ubuntu 12.04 LTS worked.

Fortunately I was able to figure this out and get over the 'hung installation' hump.

Unfortunately I'm left with no real resolution as to what the installation was getting hung up on with those options left in their default configuration.  It would be nice if I knew whether this was some weird bug with the install CD, some piece of hardware not playing nice with Unbuntu, etc.  

Thanks again for the response.

---

### Post by cortman on 2013-02-25
Glad to know you got it working.
It would appear to be a hardware issue. I quote-

> First released in December 1996, ACPI defines platform-independent interfaces for hardware discovery, configuration, power management and monitoring. The specification is central to Operating System-directed configuration and Power Management (OSPM), a system implementing ACPI, which removes device management responsibilities from legacy firmware interfaces.

Seems the ACPI built into the kernel doesn't play well with some hardware. No surprises there, it's similar to not kernel drivers for various pieces of hardware.

If this solves the issue for you, please mark the thread [SOLVED] using the thread tools in the upper right.
Good luck!

---

### Post by jeremyinrenton on 2013-02-26
> **cortman said:**
> If this solves the issue for you, please mark the thread [SOLVED] using the thread tools in the upper right.
Good luck!

Done.  Thank you.

---

