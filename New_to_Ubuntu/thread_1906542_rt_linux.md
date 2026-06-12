---
title: "rt linux?"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by bjje on 2012-01-09
I was told that ubuntu no longer supports a real time kernel as of the current distro. Does anyone have any background on this? Not having a real time clock will preclude it's use for certain scientific applications and make it a lot less fun. Anyone know anything?

---

### Post by M!K3_$ on 2012-01-09
[https://wiki.ubuntu.com/RealTime]("https://wiki.ubuntu.com/RealTime")

Doesn't look like it. But you can still compile it in.

---

### Post by Paqman on 2012-01-09
Looks like there is a [PPA for a realtime kernel]("https://launchpad.net/~abogani/+archive/realtime") on Precise, but this is a vanilla kernel from upstream, not an Ubuntu kernel.

---

### Post by sandyd on 2012-01-09
> **bjje said:**
> I was told that ubuntu no longer supports a real time kernel as of the current distro. Does anyone have any background on this? Not having a real time clock will preclude it's use for certain scientific applications and make it a lot less fun. Anyone know anything?
Compile it yourself.

Look here -> [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
Get the packages needed to compile the kernel.
Download the Ubuntu kernel.

Go to [http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/) , and get the corresponding patch (match the versions)
Place the corresponding patch into the folder.

Patch it.

Follow the rest of the instructions (past the modifying section)

Done.

---

