---
title: "Unstable OS - compatability issue with laptop?"
date: 2020-04-07
forum: New to Ubuntu
---

### Post by ryan.t.hulme on 2020-04-07
Hello all,

I have a HP laptop, bought new without OS, on which I installed Ubuntu 16.04 LTS (now updated to 18.04). From the start, the system has been buggy and often crashes in various ways - black screen on wake-up from pause; mouse still moving but unable to click on anything; or complete freeze. For each type of crash, it will not react to any of the 'Get out of an Ubuntu crash' tricks that I've found online, such as Ctrl + Alt + F3 or Alt + SysRq + REISUB - and there is no option but to simply hold down the power button to turn the system off.

It has also been through a phase of freezing during startup that Google search suggested was due to graphics card issues (fixed by changing the Grub file to 'nomodeset' following instructions from a YouTube video). Watching video and viewing images is usually no problem, but the graphics have always looked 'washed out'.

Could Ubuntu just be unsuitable for this laptop? Any ideas on how to improve things would be much appreciated.

_**Laptop/System Details:**_
Ubuntu 18.04.4 LTS
Memory: 3.8 Gb
Processor: AMD E2-9000e Radeon r2, 4 compute cores 2c + 2g x2
Graphics: AMD Stoney
GNOME: 3.28.2
OS: 64-bit
Disk: 983.4 Gb

---

### Post by Autodave on 2020-04-07
If this is a really new model, you may want to try 19.10 on it until 20.04 comes out later this month or next.  It normally takes a little while until the newest drivers are in the release.  So, if this is a really new model, you may need the newest Ubuntu release ti make it work properly.

---

### Post by ryan.t.hulme on 2020-04-08
> **Autodave said:**
> If this is a really new model, you may want to try 19.10 on it until 20.04 comes out later this month or next.  It normally takes a little while until the newest drivers are in the release.  So, if this is a really new model, you may need the newest Ubuntu release ti make it work properly.

The laptop is about a year old, so probably not due to that. It's been buggy no matter what version has been on it so far. I'll see if I can update it to 19.10 anyway.

---

### Post by ryan.t.hulme on 2020-04-08
Update - it has just crashed again while performing software updates (via Software Updater) with no other programs running. It crashed when downloading linux-headers-5.30.46. No option but to turn off via the power button, probably damaging the system.

---

### Post by CelticWarrior on 2020-04-08
A few steps to improve performance:
[LIST]
[*]Update UEFI ("BIOS") -> Some of the symptoms strongly suggest a "buggy" firmware rather that OS, software or drivers.
[*]If using a SSD* also look for updated firmware.
[*]Prefer the newest Ubuntu rather than a 4 years old OS regardless of up-to-date kernels.
[*]**Always install in UEFI mode** (disable Legacy/CSM support in UEFI and also Secure Boot
[/LIST]


* If you're using a traditional HDD you need to adjust your expectations regarding performance accordingly -> It will always be slow.

---

### Post by tea for one on 2020-04-08
> **ryan.t.hulme said:**
> For each type of crash, it will not react to any of the 'Get out of an Ubuntu crash' tricks that I've found online, such as Ctrl + Alt + F3 or Alt + SysRq + REISUB - and there is no option but to simply hold down the power button to turn the system off.

Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing a file:-

```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```

Then change the number in line 26 from 176 to 244 i.e. **kernel.sysrq = 244**

I found the solution at this site approx 12 months ago [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by ryan.t.hulme on 2020-04-08
> **CelticWarrior said:**
> A few steps to improve performance:
[LIST]
[*]Update UEFI ("BIOS") -> Some of the symptoms strongly suggest a "buggy" firmware rather that OS, software or drivers. 
[*]If using a SSD* also look for updated firmware. 
[*]Prefer the newest Ubuntu rather than a 4 years old OS regardless of up-to-date kernels. 
[*]**Always install in UEFI mode** (disable Legacy/CSM support in UEFI and also Secure Boot 
[/LIST]


* If you're using a traditional HDD you need to adjust your expectations regarding performance accordingly -> It will always be slow.

Thanks!
- Regarding UEFI update, does this link look legit? [https://www.pcinside.info/how-to/motherboard-how-to/update-motherboard-bios-uefi/](https://www.pcinside.info/how-to/motherboard-how-to/update-motherboard-bios-uefi/)
- Not so worried about speed of the system, just don't want to have to keep turning it physically off and on
- Ubuntu now 18.04 LTS and up-to-date until this new one comes out in April
- Install what in UEFI mode? The UEFI update or programmes in general?

---

### Post by CelticWarrior on 2020-04-08
The only legit website for updates (BIOS/UEFI and drivers)m is the vendor's website.

And regarding "UEFI mode", it's applicable to the OS itself.

---

### Post by Autodave on 2020-04-08
Instead of trying to upgrade to 19.10, do a fresh install of 19.10.

---

### Post by CelticWarrior on 2020-04-08
> **Autodave said:**
> Instead of trying to upgrade to 19.10, do a fresh install of 19.10.

+1

And before doing so, open UEFI ("BIOS") and disable Secure Boot and any reference to "Legacy" or "CSM". This assures you'll be booting the installer and then installing in UEFI mode.

---

### Post by Impavidus on 2020-04-08
> **ryan.t.hulme said:**
> The laptop is about a year old, so probably not due to that. It's been buggy no matter what version has been on it so far. I'll see if I can update it to 19.10 anyway.If the laptop is a year old, it's more recent than Ubuntu 18.04, which qualifies as really new.

> **ryan.t.hulme said:**
> Update - it has just crashed again while performing software updates (via Software Updater) with no other programs running. It crashed when downloading linux-headers-5.30.46. No option but to turn off via the power button, probably damaging the system.So you appear to be running kernel 5.3. That's the kernel belonging to Ubuntu 19.10 and 18.04 with HWE stack. It's the most recent kernel for any released Ubuntu, but already half a year old. Things might improve with Ubuntu 20.04, which has kernel 5.4.

> **CelticWarrior said:**
> 
[LIST]
[*]**Always install in UEFI mode** (disable Legacy/CSM support in UEFI and also Secure Boot. 
[/LIST]
 UEFI mode is the more modern and has some improvements, in particular for people dual booting, but two warnings must be given:
- Some of the earliest UEFI hardware (around 2010-2012) didn't conform very well to any standard, so with such hardware legacy mode may work better.
- When dual booting, all systems must be installed in the same mode. If you already have an OS in legacy mode and don't want to reinstall it, add new systems in legacy mode.

---

### Post by CelticWarrior on 2020-04-08
> **Impavidus said:**
> 
 UEFI mode is the more modern and has some improvements, in particular for people dual booting, but two warnings must be given:
- Some of the earliest UEFI hardware (around 2010-2012) didn't conform very well to any standard, so with such hardware legacy mode may work better.
- When dual booting, all systems must be installed in the same mode. If you already have an OS in legacy mode and don't want to reinstall it, add new systems in legacy mode.

Agreed 100% but not applicable to this system. AMD APUs really want UEFI mode. They're designed for Windows and do not work in BIOS/Legacy mode properly, never did, never will. In Windows with updated drivers they work beautifully and have a great value for the money. In desktop Linux... Well... Support has been improving with newer kernels and that's why we're always recommending the newest Ubuntu.

---

### Post by leok2 on 2020-04-10
I would suggest the HP support site and see if you need to upgrade the BIOS..
[https://support.hp.com/us-en/drivers](https://support.hp.com/us-en/drivers)

---

