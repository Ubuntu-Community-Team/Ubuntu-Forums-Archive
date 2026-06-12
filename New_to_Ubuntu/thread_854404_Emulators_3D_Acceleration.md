---
title: "Emulators 3D Acceleration?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by chris062689 on 2008-07-09
I hear that VMWare Fusion recently got the ability to hardware render in DX9?
Is this true?  How well does it work?
Is there such a thing for Linux yet?

---

### Post by pytheas22 on 2008-07-09
We tried it at work once.  It did work in that hardware-accelerated programs (AutoCAD) ran inside a Windows XP virtual machine, but the speed was extremely slow and made it pretty much not usable--and the hardware that it was running on was extraordinarily fast.  We didn't try other programs, however, so it could just be AutoCAD that's slow.  We also didn't try too hard to troubleshoot it; maybe we just needed to hack some stuff to get it to work faster.

VMware for Linux also boasts experimental support for hardware acceleration, but I've never come close to getting it to actually work.

On the other hand, wine had its first stable release (after fourteen years of development) recently, and wine does support 3D-acceleration.  You can take a look in the [wine database]("appdb.winehq.org") to see how well the programs that you want to run are supported by wine.

---

### Post by chris062689 on 2008-07-09
Yeah; trust me, I know all about WINE :)
The problem is; they've seemed to have tons of regressions dealing with the Source engine lately :(
I think... I'm going to install WINE and try out my games, and if they don't work, I guess I'll just have to bite the bullet and dualboot.
I'll also put VirtualBox on Ubuntu so I can develop python apps.
(I know I could just install it on the base system, but I'd rather run it inside a VM :lolflag:)

---

