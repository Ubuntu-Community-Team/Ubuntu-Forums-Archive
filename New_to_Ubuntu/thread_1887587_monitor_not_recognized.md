---
title: "monitor not recognized"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by gribbsy on 2011-11-27
Hello. Im running kubuntu on a pc with 6 MB of ram and 500GB hard drive. My processor is an AMD Athlon II dual-core, 2.9GHz. I also have a NVidia GeForce GT 430 video card and an HP 2310m 23" HD Widescreen monitor.
After a fresh install of Kubuntu, the resolution was correct but it didn't recognize my monitor. (not a big deal). But after I enabled my NVidia card (via hardware drivers screen) I did an apt-get update && upgrade, and reboot, I end up with an unrecognized monitor and the highest resolution it will let me pick is 1024x768. I should be running 1920x1080.
Does anyone know how to adjust the resolution back to 1920x1080? It may involve editing my /etc/X11/xorg.conf but I have no clue how to do this properly.:confused:

---

### Post by vangop on 2011-11-28
What drivers did you install? Ubuntu offers a few choices for nvidia.
Try running nvidia-settings, then go to X server display configuration ->Click detect displays.
You can also adjust resolution there.

To make a fresh new Xorg.conf backup the old one, remove it and run ```
$ sudo nvidia-xconfig

```

---

### Post by crazy bird on 2011-11-28
And to get the latest Nvidia drivers add this PPA to your repository list (sources.list):
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by heldal on 2011-11-29
The most recent drivers from Nvidia (290.X) have problems recognising displays on several GPUs. Many people have had to downgrade the driver to an older version.

---

