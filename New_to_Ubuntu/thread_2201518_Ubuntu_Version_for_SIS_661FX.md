---
title: "Ubuntu Version for SIS 661FX"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-01-24
Last year I successfully ran Ubuntu 12.04 first release from a USB Flash Drive.  I just tried Ubuntu 13.10 and it would not work.

Could this be a 64 bit problem where the Celeron D 330J does not meet requirements?  Another possibility could be lack of support for PAE (Physical Address Extension) Kernels.

Did Ubuntu change requirements after version 12.04?

Would another version such as Xubuntu 13.10 work with my processor?

The PC is from 2005 and has 1 GB of memory.  The latest version of Linux Mint also failed and it apparently requires PAE support for the 32 bit ISO.

Thanks,  Ken

---

### Post by mörgæs on 2014-01-24
> **KAWill70 said:**
> 
Could this be a 64 bit problem where the Celeron D 330J does not meet requirements? 


Yes, it's a 32 bit processor. It can't digest a 64 bit ISO.

> **KAWill70 said:**
> 
Another possibility could be lack of support for PAE (Physical Address Extension) Kernels.


According to the [fact sheet]("http://ark.intel.com/products/27112/Intel-Celeron-D-Processor-330-256K-Cache-2_66-GHz-533-MHz-FSB") the processor does support PAE, so no problem here. Did you try a 32 bit X/Lubuntu 13.10?

---

### Post by KAWill70 on 2014-01-25
I just tried Xubuntu 13.10 32 bit and it also failed.  Ubuntu 13.10 was also the 32 bit version and it failed the same way.

In both cases I get a message during boot that says SIS 630 Compatible Bus Not Detected and Module Not Inserted.  Does that mean I have an incompatible video system on this PC?

Next I will go back to Ubuntu 12.04 32 bit which worked last year.  However, I assume I will now get the third release.  If it has the same system requirements as the first release it should work.

Any other suggestions for a Linux Version that might work?  Would prefer a 13.10 release if possible.

Thanks, Ken

---

### Post by KAWill70 on 2014-01-25
My Video is based on SIS 661FX.  Would that be compatible with SIS 630 as required by Ubuntu?

---

### Post by mörgæs on 2014-01-25
SIS graphics has always been a problem and in the latest releases it's only getting worse. There are [workarounds]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464"), but I have not tried them myself.

I agree that one should normally use the newest software possible, but in this case I suggest Bodhi Linux based upon Buntu 12.04. It is very light and supported through 2017; might be the best option for the troublesome card.

---

### Post by KAWill70 on 2014-01-25
Thanks very much for all the help.  I'll try Bodhi Linux after one more try with Ubuntu 12.04.

I just tried the desktop 32 bit version of Ubuntu 12.04.3 and it also failed.  One warning during boot was displayed about the floppy drive.

This is interesting because version 0 worked for me last year.  I'm now downloading version 0 to try it again.  I wouldn't expect significant changes between version 0 and version 3 but perhaps that is an incorrect assumption.

---

### Post by KAWill70 on 2014-01-25
Latest update - Ubuntu 12.04.0 32 bit works in this system on a Flash Drive.

Ubuntu 12.04.3 does not work.

Both get the same warning about the floppy drive during boot so that must not be a problem.  Looks like Version 3 made enough changes to affect operation in my system.

Now downloading Bodhi Linux.

---

### Post by mörgæs on 2014-01-26
If the floppy drive is a problem you could try disabling it in BIOS.

---

### Post by KAWill70 on 2014-01-26
Does anyone know why Ubuntu 12.04.0 would work in this system but not version 12.04.3?  The software was 32 bit in both cases.

Would changes to graphics support be expected between revisions of the same release?

On a side note, I tried the latest Bodhi Linux and it works just great.  Web browser also very fast.

Thanks,  Ken

---

### Post by squakie on 2014-01-27
> **KAWill70 said:**
> Does anyone know why Ubuntu 12.04.0 would work in this system but not version 12.04.3?  The software was 32 bit in both cases.

Would changes to graphics support be expected between revisions of the same release?

On a side note, I tried the latest Bodhi Linux and it works just great.  Web browser also very fast.

Thanks,  Ken

Possibly.  You could check the release notes to see if they mention it.

---

### Post by mörgæs on 2014-01-27
Good you got it working. Please mark the thread 'solved'.

---

### Post by Yellow Pasque on 2014-01-27
> **KAWill70 said:**
> Does anyone know why Ubuntu 12.04.0 would work in this system but not version 12.04.3?

12.04.3 uses a newer Xserver, so you run into the bug mörgæs linked to.

---

### Post by David_Chan on 2014-03-26
I installed 10.04LTS first then did an upgrade to 12.04.4 - it seemed to get around the SIS bus problem.

---

### Post by KAWill70 on 2014-03-27
> **David_Chan said:**
> I installed 10.04LTS first then did an upgrade to 12.04.4 - it seemed to get around the SIS bus problem.
Thanks very much for passing that along.  I was looking into purchasing a video card but will try the upgrade solution that you suggested.  Hopefully this solution would work with any Linux version based on Ubuntu.

I wonder why the upgrade solution works unless it is simply the case of an earlier SIS driver staying on the system.  One concern might be that later versions of Ubuntu offer graphics features not supported by the earlier SIS graphics adapter.

---

### Post by mörgæs on 2014-03-30
If you want to try the workaround for 13.10 there are instructions in the 'old hardware' link in my signature,

---

### Post by KAWill70 on 2014-03-30
> **mörgæs said:**
> If you want to try the workaround for 13.10 there are instructions in the 'old hardware' link in my signature,

That looks like it will be a great help.  I just tried the lspci command that was specified and it displayed exactly what was shown in your "old hardware" thread.

"01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"

I don't know what the 01:00.0 code means, if anything, but it appears that I can enter the five sudo commands shown in that thread, reboot, and resolve the problem.

Would this be done by booting in compatibility mode, entering the commands, and then rebooting in normal mode?

Is a minimal iso absolutely required or could one proceed with a lighter version of Ubuntu?  I hope this solution might also work on other Linux versions based on Ubuntu.

Many thanks for providing this potential solution.

---

### Post by mörgæs on 2014-03-30
The essential part is adding the PPA, updating and dist-upgrade. It does not have to be the minimal ISO.

If it works then please vote in Launchpad.

---

