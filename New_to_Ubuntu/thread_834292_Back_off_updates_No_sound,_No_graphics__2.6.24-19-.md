---
title: "Back off updates? No sound, No graphics  2.6.24-19-386"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Rorke on 2008-06-19
First post, so sorry if I seem stupid. I applied a load of updates in a panic to try to get VirtualBox working again and now I have no sound and no Graphics card, just Generic with 800*640 res. Can I remove updates (bearing in mind I don't know which ones I applied). Help much appreciated, but I don't yet understand things like 'just untar the repository and re-compile', so idiot language prefered. I'm runnign 2 machines, and it seemed to work on the other one.
I get sound from the Ubuntu live CD.

Here's some debug stuff:
jackie@jackie:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
jackie@jackie:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
jackie@jackie:~$ uname -a
Linux jackie 2.6.24-19-386 #1 Wed Jun 4 15:54:02 UTC 2008 i686 GNU/Linux

---

### Post by sports fan Matt on 2008-06-19
I had to go back to 18 myself in symnaptic so you arent alone...

---

### Post by mvavrik on 2008-06-19
> no Graphics card, just Generic with 800*640 res

I'm having the same issue.  Some information may be available here:  

[http://ubuntuforums.org/showthread.php?t=833978]("http://ubuntuforums.org/showthread.php?t=833978")


> I had to go back to 18 myself in symnaptic so you arent alone...  

I apologize, but how in symnaptic did you do this?  I was going through it last night trying to "roll-back" the effects of the .19 kernel.

---

### Post by Rorke on 2008-06-20
Even when I go back to 18, I still have no graphics. I get 'Your screen and Graphics card could not be detected correctly, you have to configure the display yourself' - something which I am unable to do - for lack of knowl;edge, so if anyone knows, I'd appreciate a pointer. Thanks

---

### Post by hyper_ch on 2008-06-20
try
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Rorke on 2008-06-20
I get Package 'phigh' is not installed and no info is available.
Hmm?

---

### Post by hyper_ch on 2008-06-20
it's the other way aruond
```

sudo dpkg-reconfigure xserver-xorg -phigh

```

---

### Post by Rorke on 2008-06-20
Doh! OK - I'm back on the other PC now, so no reading errors.
I get >
sudo dpkg-reconfigure xserver-xorg -phigh
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080620113920
and now I have 'Not in Use' written by the nvidia device driver in the hardware device manager.

---

### Post by hyper_ch on 2008-06-20
then re-enable it again with the restricted driver manager

---

### Post by Rorke on 2008-06-20
OK, it seems like I'm getting closer.
I think I re-enabled it using the standard Hardware Drivers manager.
I re-booted, and got into the grub menu.
I have a loag of 'generic' kernels from 16 to 19, but also the default one is '386' not 'generic'. When it boots this one, I get no sound andundetected graphics.
When I booted into '19' 'generic' I got good graphics resolution and sound for the password page, but then as it was booting I got a 'no signal' from the screen and had to remove power to re-boot.
I'm going to try re-booting into '18' 'generic', but I think I already tried that.

---

### Post by Rorke on 2008-06-22
Hi, I tried re-enabling the nvidia card, but when I reboot, I get a high res screen for the login then no signal at all after Ubuntu boots. The only way to fix it is to load the repair boot and do a Xserver repair, where it overwrites the configuration. Do you have any other ideas?
Thanks

---

### Post by Rorke on 2008-06-22
This isn't the same problem as when I started the thread, so I'm going to close it and look around for the remaining problem. I don't know how to close it though.

---

