---
title: "Will wubi compatible with Windows 8 ?"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by lolly325 on 2012-01-15
I'm still curious why windows 8 block linux to dual boot...
But is that possible ?
Because, in the future, windows 7 will no more and replaced with 8.
And many news are coming about windows 8 will block linux.
Is there any way ? Can wubi having dual boot with windows 8 ?

---

### Post by bluexrider on 2012-01-15
As I understand it, Windows 8 compatibility on Microsoft Certified Hardware will be locking out Linux.

---

### Post by lolpenguin on 2012-01-15
As of now, the plan is that an OEM install of Windows 8 will use secure boot, which will not allow any [unauthorised] changes to the boot sector, so malware cannot run before the OS is loaded (as well as not allowing non-Microsoft bootloaders (ie GRUB or anything used for GNU/Linux) to load). This MAY change in the future, but it doesn't seem likely.

---

### Post by androssofer on 2012-01-15
> **lolpenguin said:**
> As of now, the plan is that an OEM install of Windows 8 will use secure boot, which will not allow any [unauthorised] changes to the boot sector, so malware cannot run before the OS is loaded (as well as not allowing non-Microsoft bootloaders (ie GRUB or anything used for GNU/Linux) to load). This MAY change in the future, but it doesn't seem likely.

here is what M$ says about is:

> 
MANDATORY: Enable/Disable Secure Boot.

On non-ARM systems, it is required to implement the ability to disable Secure Boot via firmware setup. A physically present user must be allowed to disable Secure Boot via firmware setup without possession of Pkpriv. Programmatic disabling of Secure Boot either during Boot Services or after exiting EFI Boot Services MUST NOT be possible.

Disabling Secure MUST NOT be possible on ARM systems.

so it appears on normal x86 computers, OEMs are required to put in the option for disabling secure boot in their firmware. However on ARM devices its to be disabled. 

so it would appear wubi will be fine as long as your not buying windows 8 certified ARM hardware.

source of info : 

[http://www.omgubuntu.co.uk/2012/01/microsoft-to-prevent-linux-booting-on-arm-hardware/](http://www.omgubuntu.co.uk/2012/01/microsoft-to-prevent-linux-booting-on-arm-hardware/)

---

### Post by imagecko on 2012-01-15
It is well known that Microsoft always has tried to ban Linux.

---

### Post by androssofer on 2012-01-15
> **imagecko said:**
> It is well known that Microsoft always has tried to ban Linux.

true.but I can see where they are comming from on the ARM thing. 

as apple does the same, it uses secure boot on IOS for the purpose of stopping android running on its devices. and i think M$ wants to do the same.. 

Basicly its a sign they are gettin scared of Linux... the age of the desktop is over, Servers and mobile is the future and Linux already owns Servers but android is the only big Linux player in mobile, so M$ wants to stamp that out...

---

### Post by Frogs Hair on 2012-01-15
I read that MS is trying to create a gated community like Apple with a Line of products possibly including proprietary pc's . I think compatibility with anything they don't own piece of or generates a profit is threatened .

With that in mind , why would MS  allow a person to continue to try  free operating systems via a windows installer . The days of any kind of dual boot may be numbered .

---

### Post by androssofer on 2012-01-15
> **Frogs Hair said:**
> I read that MS is trying to create a gated community like Apple with a Line of products possibly including proprietary pc's . I think compatibility with anything they don't own piece of or generates a profit is threatened .

With that in mind , why would MS  allow a person to continue to try  free operating systems via a windows installer . The days of any kind of dual boot may be numbered .

you could say the same about apple, but they openly allow Linux and windows on their hardware via bootstrap.

M$ are idiots, most people who dual boot are gonna buy the hardware anyway, with windows pre-loaded, so they r making their money. So by stopping it you just **** people off... and pissed of people is bad for business.

---

### Post by Frogs Hair on 2012-01-15
> **androssofer said:**
> you could say the same about apple, but they openly allow Linux and windows on their hardware via bootstrap.

M$ are idiots, most people who dual boot are gonna buy the hardware anyway, with windows pre-loaded, so they r making their money. So by stopping it you just **** people off... and pissed of people is bad for business.

I hope you are correct about that .

---

### Post by Mark Phelps on 2012-01-15
> **lolly325 said:**
> I'm still curious why windows 8 block linux to dual boot...Is there any way ? Can wubi having dual boot with windows 8 ?

Wubi is NOT the same as traditional dual-boot, and everyone here QUICK to respond failed to notice this ...

Wubi installs Ubuntu like any other app. So, to stop this, MS would have to prevent the installation of apps ... and even MS is NOT going to do that.

As to the OTHER question -- the one the posters actually answered -- apart from ARM machines, there is no concrete answer yet.  While it's likely that some OEMs will block this, in the same manner thay they preload PCs with 4 primary partitions, ways will be found to work around the limitations they impose.

---

### Post by pqwoerituytrueiwoq on 2012-01-15
will this firmware be on the hard drives? if so we can just use a second hdd
anyway as Mark Phelps said wibi install just like a app
> Wubi installs Ubuntu like any other app. So, to stop this, MS would have  to prevent the installation of apps ... and even MS is NOT going to do  that. i do agree at least as long as they don't have a 100% market share

---

### Post by halitech on 2012-01-15
even if OEMs give in and do what M$ wants, the way around it is to not buy OEM machines, buy your own parts and build yourself and then run a hacked version of Windows 8 (I imagine someone will crack it within days of being released) that is set up so you can run both.

---

