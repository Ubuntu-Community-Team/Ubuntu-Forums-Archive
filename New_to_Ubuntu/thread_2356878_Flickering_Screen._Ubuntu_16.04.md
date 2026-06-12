---
title: "Flickering Screen. Ubuntu 16.04"
date: 2017-03-27
forum: New to Ubuntu
---

### Post by aris-ko on 2017-03-27
I just installed Ubuntu 16.04 and i have problem with flickering screen. These are the specifications of my laptop.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial

DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"

Linux SVF15 4.8.0-41-generic #44~16.04.1-Ubuntu SMP Fri Mar 3 17:11:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
    Subsystem: Sony Corporation Haswell-ULT Integrated Graphics Controller [104d:90be]
    Kernel driver in use: i915

DESKTOP_SESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=Unity

Any help will be appreciated!

---

### Post by RobGoss on 2017-03-27
Hello and welcome to the forum, Does this happen when you browse the web? I did a search regarding this issue and came across this post [http://askubuntu.com/questions/766725/annoying-flickering-in-16-04-lts-chrome](http://askubuntu.com/questions/766725/annoying-flickering-in-16-04-lts-chrome) If might be helpful and worth a read

---

### Post by aris-ko on 2017-03-28
Not only when i browse the web but even if im in settings or home page. In general everywhere.

---

### Post by mörgæs on 2017-03-28
Do you see the same in a live boot of 17.04 (beta)?

---

### Post by RobGoss on 2017-03-28
Please run the following command:
post the output using the **code tags**

```
 lshw -C video
```

---

### Post by aris-ko on 2017-03-28
I have 2 graphic cards(Intel and nvidia).My system could only see the Intel card and so i disabled the nvidia 
I also just noticed that my screen will flicker if i dont move my mouse. If mouse is moving everything is fine

[CODE][]
  *-display                      description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:b3000000-b33fffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: GK208M [GeForce GT 740M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nouveau latency=0
       resources: irq:50 memory:b2000000-b2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128)

---

### Post by aris-ko on 2017-03-28
Ok guys. Thanks for your help. I think i solved the problem buy installing the 4.4 kernel

---

### Post by RobGoss on 2017-03-28
That's great thanks for sharing your solution

---

### Post by mörgæs on 2017-03-29
Still it would be interesting to know how it works in 17.04. If there are problems then a bug report will be appreciated.

---

