---
title: "Does autorun.inf and other USB Viruses will run in Ubuntu?"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by SkyLinePH on 2011-11-27
I'm just curious if those autorun.inf and other USB viruses will run in Ubuntu.:KS

---

### Post by LowSky on 2011-11-27
only if you let them

---

### Post by dagoth_pie on 2011-11-27
Short answer no,
the long answer involves me accidently giving viruses to people because I'd assumed my external hard drive was clean. It's a good idea to install a free antivirus specifically to protect Windows users that you'll share files with. I believe there's quite a few that are designed for servers.

---

### Post by The Cog on 2011-11-27
I think that at the moment, Ubuntu is safe from this kind of problem. That's not to say there won't be a problem in the future, but I don't think there is one now. For two reasons:

1: Most malware is aimed at windows and to a lesser extent OSX, not Linux.

2: Linux doesn't normally autorun software so some other flaw must be found first in order to get malware to run. 

Some months ago, something akin to autorun was demonstrated on Linux. It used hundreds of PDF malformatted files on a USB stick, and a flaw in the PDF viewer that created the thumbnail images in the browser window. I believe the flaw has been fixed since then. So autorun is Linux is not as easy as in windows, but there are always new weaknesses to be found.

---

### Post by SkyLinePH on 2011-11-27
Thanks for your feedbacks guys.

---

### Post by mike555 on 2011-11-27
If a person has "Wine" installed on Linux and if he clicks on something bad then it might run enough to mess up things in his /home folder.... but not hurt the Linux operating system .

---

### Post by SkyLinePH on 2011-11-28
> **mike555 said:**
> If a person has "Wine" installed on Linux and if he clicks on something bad then it might run enough to mess up things in his /home folder.... but not hurt the Linux operating system .
WOW Sounds nice. :popcorn:

---

### Post by beew on 2011-11-28
> **mike555 said:**
> If a person has "Wine" installed on Linux and if he clicks on something bad then it might run enough to mess up things in his /home folder.... but not hurt the Linux operating system .

Well that would be quite an accomplishment, to have something working flawlessly in WINE. :) Such a virus should be featured as "platinum" on WHQ's list. :)

---

### Post by crazy bird on 2011-11-28
> **LowSky said:**
> only if you let them
 
Wrong answer if we're talking about Windows virusses. 
 
Windows virusses won't affect a Linux installation due to the fact that the architecture of Windows differs from the architecture of Linux. The only thing a Linux user must be aware of is the fact that when the Linux user saves an infected file, the virus will not be destroyed. The saved data of the file will not be damaged or altered, this includes virusses too. So, if a Linux user send such infected file to a Windows user, the Windows user will be infected with it. 
 
Although there are some Linux virusses "alive", the chance of getting them is negligible. And even if you get infected by a Linux virus, then to get activated, the virus must find a way around the security system (right management system) of Linux.
 
Autorun.inf files are purely ment for Windows systems, not for Linux. Again, all software written for Windows will not run on Linux. Only by using a tool like Wine you are able to run most Windows software since Wine emulates the API environment of Windows. Else you have to use a dualboot system or using a tool such as Virtualbox to install Windows within a virtual environment.
 
Keep in mind that virusses do have an effect on Windows installed in a virtual environment or programs running under Wine.

---

### Post by SkyLinePH on 2011-11-29
Thank you very much guys.

---

