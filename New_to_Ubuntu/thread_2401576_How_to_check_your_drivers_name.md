---
title: "How to check your drivers name"
date: 2018-09-19
forum: New to Ubuntu
---

### Post by awesomegamer2018 on 2018-09-19
I just installed ubuntu but theres a issue theres no sound. I need help to find out whats my driver name. I have two sound card but i use amd/ati

00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
    Subsystem: Dell Sunrise Point-H HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 131
    Memory at df320000 (64-bit, non-prefetchable) [size=16K]
    Memory at df300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

--
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aae0
    Subsystem: XFX Pine Group Inc. Device aae0
    Flags: bus master, fast devsel, latency 0, IRQ 130
    Memory at df260000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

---

### Post by MoebusNet on 2018-09-20
I am NOT an expert. But until someone can offer better advice, I would use Synaptic Package Manager to search for a package containing your card's description. If installed, it would list the name of your driver. I am sure that there is some CLI method of more precisely identifying the sound driver in use, but I don't know what that would be. There is a subforum for multi-media software in the forum; that might be a good place to research. Best of luck!

---

