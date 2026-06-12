---
title: "How to dual boot ubuntu and anything else (how much RAM required?)"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-26
Hi

What I wanted to know is how to dual boot Ubuntu and anything else(not sure which OS to use) and how much RAM it requires to do it.

Complete computer NOOB so any help would be appreciated!

---

### Post by Mhurst1 on 2008-05-26
[Here]("http://en.wikipedia.org/wiki/Dual_boot")

---

### Post by lswest on 2008-05-26
Well, the dual boot means that the amount of RAM you need is the maximum minimum spec for any of the OSes on your computer.  E.g. if you're dual booting Ubuntu (min. RAM about 384MB) and Vista (min. RAM about 1GB and 2GB is recommended) you would need 1-2GB of RAM.  As for how to do it, basically you partition your drive so it has 1 partition per OS (if dual-booting multiple Linux OSes you can set up 1 swap and 1 home partition for them all and share them).  When you install a second Linux OS, be sure to install GRUB to the partition you're installing it to, and not the MBR (should be an option on many Linux distros) and if you are installing a Windows OS for the dual boot, be sure to look at on how to restore GRUB (i wrote a how-to on it, 3rd line of my sig).  Also, it's always best to google the exact config once you decide on an OS to dual boot with, just to make sure there aren't any strange tweaks you need.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-26
Getting Ubuntu I feel reluctant of switching back to Windows XP and I have Fedora 8 and Debian CDs too! I need some kind of advice of which one to choose:confused:

---

### Post by lswest on 2008-05-27
Well, if you want try something completely different, try Gentoo, Arch, or Fedora (as it runs on the rpm base, not a debian base).  Debian is similar to Ubuntu (since it was based on Debian) and comes with less pre-installed (Arch does as well, but is very different).  Ultimately, it's your choice, just choose one and go ;)

---

