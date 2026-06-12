---
title: "Has anyone use Heron on the new p43 or p45 intel chipsets"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by astroorion on 2008-06-27
I am looking into building a new computer here in the next few week's.
I am wondering if Heron will run on the new intel P43 and P45 chipset I know it's close to the P35 I would like to make it also into a dual boot with xp pro 32 bit.
I have been lucky with my old motherboard being that I can hit F11 and boot Ubuntu Manually Or Xp using two diffrent hard drives One for Xp and one for Ubuntu
Any Info would be helpful since I refuse to use window's XP for the internet EVER LINUX :guitar:

---

### Post by Canis familiaris on 2008-06-27
No I havent tested these platforms. But Intel chipsets work really well with Linux. But wait better to be sure.

Perhaps the guys at Phoronix will test these chipsets in Linux.

[http://www.phoronix.com](http://www.phoronix.com)

---

### Post by mjwhitfield on 2008-06-27
> **astroorion said:**
> I am wondering if Heron will run on the new intel P43Built a workstation based on the P43.  Just surfing, browsing, music.  Worked fine.

---

### Post by pdub on 2008-06-27
I just installed Hardy 64bit on an ASUS P5Q Deluxe and it worked fine. I did have to set the SATA drives to AHCI in the BIOS first, otherwise the partition manager did not see any drives.

---

### Post by OsireS on 2008-07-05
Hi

Like it was reported below on my new EP45-DS3R the standard hardy heron installer does not see my HDD at all unless I enable AHCI (which prevents Windows XP from booting as it was installed when AHCI was disabled).

I was wondering if there was a way of either getting the partition manager in the installer to see my HDD when AHCI is not enabled or afterwards to get the kernel to boot when I switch off AHCI (as the kernel seems to hang when botting up if I switch of AHCI, it finishes initliasing all the USB components and then just hangs). 

Any help would be greatly appreciated.

---

### Post by zzatz on 2008-07-05
Ubuntu and GRUB should see your drives if the BIOS is set to either AHCI or IDE. The factory XP disc will only see IDE.

I suggest setting the BIOS to AHCI and putting the XP SATA drivers on a floppy, or slipstream them onto a new XP installation disc. See the usual Windows sites for more.

---

### Post by OsireS on 2008-07-06
Do be honest just did a clean reinstall as this is a new PC and after having spent the better part of the day reinstalling all my apps I'm rather loath to have to do it all over again ;)

Also I've tried almost everything to get Ubuntu to see the drive without AHCI enabled and it seems almost impossible (native and legacy mode tested, along with a good couple of param switches). It seems HH cannot see any HDD when using this new P45 chipset (ICH10) and has issues with the onboard network (although that has been resolved, there are two and it can only acceess eth0 not eth1).

Installer can't see the drive, LiveCD booted cannot see the drive and I've tried mod-probing / adding in extra drivers to make sure it just didn't detect it properly but it seems that it definetly has issues with ICH10 and Ubuntu. Anybody know of any patches out there right now?

---

### Post by astroorion on 2008-07-17
Thank's For all the responses I have been playing around with my new hardware a biostar p43 tseries motherboard and like everyone has said to enable ahci which I have to get Ubuntu to see the hard drive of course I installed Xp without the F6 sata driver's and it see's the Ide setting no biggie though can allway's reinstall Xp.
Only one wish I hope Ubuntu will take over on the game Market cause if that happen's then I know Microsuck will founder with there Drm :guitar:

---

