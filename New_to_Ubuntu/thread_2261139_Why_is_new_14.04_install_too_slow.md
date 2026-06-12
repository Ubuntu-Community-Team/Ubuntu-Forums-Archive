---
title: "Why is new 14.04 install too slow?"
date: 2015-01-16
forum: New to Ubuntu
---

### Post by Jose_Chajchalac on 2015-01-16
Help !!!!!!!!!


I just installed Ubuntu LTS 14.04.01 32bit on a PC with AMD processor and 4 GB of RAM, installing and loading does it well, but since when is too slow to be manipulating someone to tell me which may be wrong, will thank you much

---

### Post by DuckHook on 2015-01-16
Need more info to help effectively. But even without it, I am assuming that you have an older machine that can only run 32-bit OSes. You have lots of RAM but don't mention exactly what kind of AMD processor. Old vs new makes a huge difference. Also missing a very important piece of info which is the video subsystem (both GPU and amount of dedicated VRAM, if any).

At first blush, I would say that your machine is not powerful enough to run Ubuntu, but given lack of system info, this is just a wild guess. You may be better off with Xubuntu or Lubuntu.

Please provide complete detailed system specs and we can go from there.

---

### Post by CantankRus on 2015-01-16
..adding to DuckHook's post,
you can install inxi to display some details.
Install via terminal....
```
sudo apt-get install inxi
```

Then in terminal run...
```
inxi -b
```

and post your output...
eg
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **inxi -b**
System:    Host: Trusty Kernel: 3.13.0-39-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1400.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.113
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1254.2GB (14.0% used)
Info:      Processes: 263 Uptime: 19:22 Memory: 1756.2/3935.1MB Client: Shell (bash) inxi: 1.9.17
```

---

### Post by DuckHook on 2015-01-16
> **CantankRus said:**
> ...you can install inxi to display some details...CantankRus, this is an awesome little app and after all these years up until today *I did not know it existed*. Bravo! I'll be using (and suggesting) it from now on. So much easier for new users than the usual sudo lshw/lspci gobbledegook. Aside from a few dependencies which are no big deal, this is so cool. Thanks for sharing.

---

### Post by Bucky Ball on 2015-01-16
Welcome Jose_Chajchalac. I have changed the title of your thread to give you a better chance of getting support. Descriptive thread titles work best (most people here want help). ;)

Just wondering, as you have 4Gb of RAM I'm guessing you have a 64bit processor. Do you? If so, why have you gone for the 32bit version of 14.04? Changing to 64bit, if appropriate, may not fix your issue, but just curious. It will utilise your hardware better, though, if it is a 64bit processor (don't know that the 32bit version can handle 4Gb of RAM).

Please follow the instructions given by CantankRus so we can have a better look at 'what's in the box'. (Thanks for the inxi heads up CantankRus. I had also never heard of it. ;))

---

### Post by CantankRus on 2015-01-16
No problem. Inxi was available as a downloadable bash script a couple of years ago
and I noticed recently it had been added to the Ubuntu repos for 14.04 and later.
I believe it's a fork of an older script **infobash**. ):P

---

