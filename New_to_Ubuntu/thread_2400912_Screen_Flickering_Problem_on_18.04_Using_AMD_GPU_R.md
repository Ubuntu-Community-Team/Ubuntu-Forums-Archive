---
title: "Screen Flickering Problem on 18.04 Using AMD GPU Rx560"
date: 2018-09-11
forum: New to Ubuntu
---

### Post by toaki on 2018-09-11
I recently switch from windows and I don't know much about Linux/Ubuntu.. Just facing a problem, my Screen is flickering too much don't know how to fix it. If anyone can solve the problem it will be a great help.

My PC Configuration:

```
:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"

$ uname -a  
Linux Astrex 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

$ lspci -nnk | grep -iA2 vga 
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Baffin [Polaris11] [1002:67ff] (rev cf)
    Subsystem: Sapphire Technology Limited Baffin [Radeon RX 560] [1da2:e348]
    Kernel driver in use: amdgpu

$ env | grep DESK
DESKTOP_AUTOSTART_ID=103e57ff8d2f514f5f153669095019193900000014230007
DESKTOP_SESSION=ubuntu
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=ubuntu:GNOME
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
```

---

