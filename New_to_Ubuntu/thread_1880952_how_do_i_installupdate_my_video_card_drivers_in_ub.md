---
title: "how do i install/update my video card drivers in ubuntu"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by jab1 on 2011-11-14
i have a radeon 9550 that i want to install the drivers for but i don't know how to do so in ubuntu

can anybody help?

i'm using the latest ubuntu release: 11.10

---

### Post by Paqman on 2011-11-14
Open up the Additional Drivers tool and see if you've got a driver there waiting to be installed. If you install an driver in this way it'll be kept updated by the normal Ubuntu update process. Although tbh graphics driver updates in a stable version are pretty rare. You're more likely to see a new driver when you upgrade to a new version of Ubuntu.

---

### Post by jab1 on 2011-11-14
the additional drivers tool found nothing, it said "no propitiatory are in use on this system"

???

---

### Post by coffeecat on 2011-11-14
> **jab1 said:**
> the additional drivers tool found nothing, it said "no propitiatory are in use on this system"

???

That's because you have an old ATI card that AMD stopped supporting with their proprietary driver in 2009:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

The only driver that will work with that card in 11.10 is the default open source driver which you already have.

---

### Post by saidbakr on 2011-11-16
Hi,
But the default driver has no any catalyst and I feel that it does not work properly, because any flash app. affects the performance very bad.
In addition, on AMD ATI website we could find drivers for ubuntu linux for Radeon 9550 SE and it downloaded as *.run file, but that file could not be installed it generates some errors.

---

### Post by alphacrucis2 on 2011-11-16
> **saidbakr said:**
> Hi,
But the default driver has no any catalyst and I feel that it does not work properly, because any flash app. affects the performance very bad.
In addition, on AMD ATI website we could find drivers for ubuntu linux for Radeon 9550 SE and it downloaded as *.run file, but that file could not be installed it generates some errors.
 
That's because the old ATI driver is not compatible with the current Ubuntu X server (and also kernel I suspect). To use the old driver, you would have to install an old version of ubuntu that came with a kernel and X server compatible with the old Catalyst driver.

---

### Post by shuttleworthwannabe on 2011-11-16
Hi sorry which "old" version of Ubuntu would you recommend--I also have an oldish ATI card that experience poor graphics performance in latest Ubuntu because of the same issues OP described.

Thanks
SwB

---

### Post by coffeecat on 2011-11-16
> **shuttleworthwannabe said:**
> Hi sorry which "old" version of Ubuntu would you recommend--I also have an oldish ATI card that experience poor graphics performance in latest Ubuntu because of the same issues OP described.

Have a look in the link I posted:

> The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

If your card is in that list, then you'll only be able to install an old version of the Catalyst driver in obsolete (pre-2009) versions of Ubuntu. But the open source driver should still work in current versions of Ubuntu.

This is not just an issue problem with ATI cards. "Old" nvidia devices can be problematic with the proprietary driver in newer Ubuntu versions. Even with Intel, where the driver is open source, older chipsets are becoming difficult. The Intel 8** series is an example.

---

### Post by mastablasta on 2011-11-16
another option is to turn off any unnecessary effects - they might be causing the flash to lag. use Unity 2D if you are on Ubuntu or switch to Xubuntu for improved performance. some old cards are nicely supported with opensource drivers while other have issues.
 
you could also install the latest version of opensoruce drivers via PPA (it's called X-org edgers) though if you have 11.10 i doubt there would be much improvement). You could also try (if you dare and have the knowledge to tinker) to use the bleeding edgers PPA (development version i believe).

---

### Post by Mark Phelps on 2011-11-16
The "last" version of Ubuntu that was able to handle restricted ATI drivers for that card was 8.10 -- and I believe that had reached end of life some time ago.

So, rather than go back to a 3-year old version of Ubuntu, either use the open source drivers (they're better in 11.10) or get a newer video card that is supported (ATI HD series).

---

### Post by shuttleworthwannabe on 2011-11-16
> **coffeecat said:**
> Have a look in the link I posted:



If your card is in that list, then you'll only be able to install an old version of the Catalyst driver in obsolete (pre-2009) versions of Ubuntu. But the open source driver should still work in current versions of Ubuntu.

This is not just an issue problem with ATI cards. "Old" nvidia devices can be problematic with the proprietary driver in newer Ubuntu versions. Even with Intel, where the driver is open source, older chipsets are becoming difficult. The Intel 8** series is an example.

Yes, my card is listed there X1250.
So it will be Intrepid, Jaunty and Maverick? Right?

---

### Post by coffeecat on 2011-11-16
> **shuttleworthwannabe said:**
> Yes, my card is listed there X1250.
So it will be Intrepid, Jaunty and Maverick? Right?

No. The cutoff time in that AMD link was February 2009. Only Intrepid (8.10) was released before then, and as Mark Phelps says, that's now unsupported. Jaunty (9.04) *might* work but that's unsupported now too. Maverick definitely out - that's only a year old.

---

