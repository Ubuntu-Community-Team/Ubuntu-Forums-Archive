---
title: "Restore Xorg"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by lolpenguin on 2011-11-12
Ubuntu 11.10 "Oneiric Ocelot"
I updated my NVIDIA drivers to NVIDIA-Linux-x86_64-285.05.09.run and now, whenever I start X Server, there is an error "No screens found". HOWEVER, I looked at Xorg.conf and both my monitors are listed. I need a way to restore Xorg to the default settings, or better, to what was before the installation of NVIDIA drivers. I think backups were made by the installer. All contributions will be helpful.

*****************************************************************

If all does not come well, I have a system image I can use to restore my system, and a duplicity backup of my home folder and a physical (older) copy of my home folder, and a live CD (which does not seem to let me boot into live desktop, but it should work).

*****************************************************************

As a postscript, I've had the same error on Arch Linux, but I was able to locate the package for the vesa drivers and boot into an X session.

---

### Post by Paqman on 2011-11-12
Ubuntu doesn't actually need xorg.conf, but it will use it if it's available. To restore it, just delete it. If you still can't boot up properly then choose the recovery option and boot into the command line then use the Additional Drivers tool in text mode.

To check what drivers are installed:
```
jockey-text -l
```
Then enable one of the drivers with:
```
jockey-text -e name-of-driver
```
You'll probably want to enable something like xorg:nvidia-XXX

---

