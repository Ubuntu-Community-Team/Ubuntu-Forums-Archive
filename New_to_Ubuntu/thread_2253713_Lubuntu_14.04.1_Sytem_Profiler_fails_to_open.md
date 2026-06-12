---
title: "Lubuntu 14.04.1 Sytem Profiler fails to open"
date: 2014-11-21
forum: New to Ubuntu
---

### Post by Herodotus2go on 2014-11-21
I don't have a lot of experience with Lubuntu.  I just recently installed Lubuntu 14.04.1 as a dual boot with Windows XP on an older Dell Demension 2400 with a Pentium 4 CPU and 768MB of RAM.  The install was a little rough due to the computer having an undetected failing case fan which was causing the CPU to overheat and lockup system.  Once this was diagnosed and corrected all seemed to be working ok.  Then today, one day after completing installation when I attempt to open the System Profiler a blank window with what looks like a blank error message briefly appears then disappears.  I though I would try removing and reinstalling package with Synaptic Package Manager but was scared to when Synaptic told me that the Lubuntu Desktop package would be effected.  I've tried rebooting the system and searching forums and web for information on this problem without success.

I will really appreciate any advice on how to correct this problem.  I'm installing Lubuntu on this computer for some older relatives who were still using Windows XP.  I really want to give them a correctly functioning machine that will be safer for them to use on-line.

Thanks,

Herodotus2go

---

### Post by Rob Sayer on 2014-11-22
Try doing a fast screen capture when the error message appears when you open the program.  Post that here.

---

### Post by Dennis N on 2014-11-22
If your problem looks like the attached image, then it might be a problem caused by the theme. A similar problem existed with the default theme (Lubuntu default) in older releases of Lubuntu, but on my system doesn't happen with Lubuntu 14.04. Your description says that the window disappears, but with the old bug, it didn't go away. So you may have something different going on. 

Dealing with the old bug (may or may not help with yours):
 
1) try a different selection in **Preferences > Customized Look and Feel > Widget** 
or
2) keep closing the smaller error box until they no longer pop up when you select something in that dialog. Then your information will appear.

---

### Post by vasa1 on 2014-11-22
I'm on Lubuntu 14.04.1 but I'm not using the default theme; I'm using Greybird heavily modified. I've never used the System Profiler before and so can't tell you whether it would have worked for me or not in earlier versions of Lubuntu. It seems to be working fine for me.

If there's some specific information you need, you can try **hardinfo** from the terminal (which is the command that the System Profiler .desktop shows in the **Exec=** line):```
[Desktop Entry]
Name=System Profiler and Benchmark
Name[pt_BR]=Informações e Testes do Sistema
Exec=hardinfo
Icon=/usr/share/hardinfo/pixmaps/logo.png
Terminal=false
Type=Application
StartupNotify=true
Categories=System;
```

I can't say more than that because I don't have experience with it. Here's what I saw with **hardinfo -r**```
$ hardinfo -r
Computer
 Summary
sh: 1: /lib/libc.so.6: not found
 Operating System
 Kernel Modules
 Boots
 Languages
 Filesystems
 Display
 Environment Variables
 Users
Devices
 Processor
 Memory
 PCI Devices
 USB Devices
 Printers
 Battery
sh: 0: -c requires an argument
 Sensors
 Input Devices
 Storage
 DMI
 Resources
Network
 Interfaces
 IP Connections
 Routing Table
 ARP Table
 DNS Servers
 Statistics
 Shared Directories
Benchmarks
 CPU Blowfish
 CPU CryptoHash
 CPU Fibonacci
 CPU N-Queens
 FPU FFT
Segmentation fault (core dumped)
```
I guess the last line says it all ;)

---

### Post by Herodotus2go on 2014-11-22
Thanks Dennis N & Rob,

Using a different widget set solved the problem.  I had downloaded and was using a windows xp theme to try and make the move to lubuntu as easy as possible for my wife's aunt and uncle.  Switching to the Redmond widet set corrected the problem and kept the look and feel of xp for them.

I can't thank you enough.  I was really dreading the possibility (at least in my mind) of having to do a clean re-install, updates, restricted-extra, etc... on the system.

Thanks again,

H2g

p.s. I am looking for thread tool to mark thread as solved but don't see it.

---

### Post by Herodotus2go on 2014-11-22
Thanks Vasa1,

I had found **hardinfo** when I was searching forums and web before starting this thread and was using it.  Thanks for the help.

Best regards,

H2g

p.s. i found the thread tool to mark the thread as solved. thanks to all.

---

### Post by mörgæs on 2014-11-22
Good that you got it solved.

> **Herodotus2go said:**
> ...told me that the Lubuntu Desktop package would be effected.

You can safely delete this package. It is sometimes referred to as a shopping list for other packages, and deleting the list after install has no effect.

---

