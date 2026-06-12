---
title: "Bug report?"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by Chris_Nickel on 2012-02-16
Hi,
I'm using Ubuntu 11.04 and have a red dot with a line through it in my top bar.
When I click on the button it says to report the following bug:

E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

So I guess my questions are: Where do I report the bug and how can I get the error icon off my screen.

Thanks

Chris_Nickel

---

### Post by Ms. Daisy on 2012-02-17
Did you just recently upgrade to 11.04 from 10.x?

Bugs get reported at launchpad.net. I would presume that you would remove the error icon by fixing the bug.

I googled the error you listed above and got this

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652)

I'd recommend reading through that, make sure it fits your problem.  It looks like they suggest this fix:
```
sudo apt-get remove xserver-xorg-video-nouveau
```
But you may want to do a little research to understand exactly what that removes.

---

### Post by audiomick on 2012-02-17
> **Ms. Daisy said:**
> Did you just recently upgrade to 11.04 from 10.x?
a little research to understand exactly what that removes.

From the Synaptic package manager:

> This driver for the X.Org X server (see xserver-xorg for a further description)
provides support for NVIDIA Riva, TNT, GeForce, and Quadro cards.

Although the nouveau project aims to provide full 3D support it is not yet
complete, and these packages do not include any 3D support.
Users requiring 3D support should use the non-free "nvidia" driver.

This package is built from the FreeDesktop.org xf86-video-nouveau driver.

---

