---
title: "Ubuntu stuck on bootsplash screen after upgrading to 11.10"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by diablo75 on 2011-12-05
My uncle has a Zotac MiniMag computer (ITX motherboard form factor; not sure of the exact model number though) and he said that he went forward with the upgrade from 11.04 to 11.10.  The upgrade completed and asked him to reboot his computer.  The computer then locks up during the bootsplash screen.  I haven't seen it in person but he told me that he can see some kind of shutdown button (like what he used to see in 10.10 I assume, and I'll also guess 11.04 if perhaps his video chipset wasn't able to handle Unity and continued running GNOME) in the upper right corner, but there's no cursor on the screen and the mouse doesn't do anything.

I have a feeling that perhaps Unity is causing a problem and his system can't support it.  Not sure what to try to do to fix this.

---

### Post by lolpenguin on 2011-12-06
I guess LightDM isn't loading correctly right?

---

### Post by diablo75 on 2011-12-06
I'm not sure what LightDM is.  There is no mouse cursor on the screen and the system acts like it's completely froze with the solid purple background and Ubuntu logo up on the screen.

---

### Post by kio_http on 2011-12-06
Hmm try the recovery mode then do

```
sudo apt-get install -f
```

if it works or else see the error message it gives.

---

### Post by diablo75 on 2011-12-06
It's my uncles computer so I'm going to have to grab it and work on it later this evening.  I'll follow up when I've run that command.  I can't remember, what key do you have to hold down to bring the grub menu up and enter recovery mode?

---

### Post by kio_http on 2011-12-06
> **diablo75 said:**
> It's my uncles computer so I'm going to have to grab it and work on it later this evening.  I'll follow up when I've run that command.  I can't remember, what key do you have to hold down to bring the grub menu up and enter recovery mode?

Shift I think

---

### Post by diablo75 on 2011-12-06
Well I've made some discoveries and long story short I've narrowed down the cause of the problem to be Linux kernel version 3.0.0-13, which will lock the system (even if I select recovery mode for that version) if you use it.  However, version 3.0.0-12 works perfectly fine.

I figure the best work around for this would be to use [Grub Customizer]("https://launchpad.net/grub-customizer") to modify the default kernel selection so it will bypass the version that has the problem.  Perhaps there's a better work around?  Or maybe an even newer version of the kernel available I could try to install manually just to see if it solves the problem caused by release 13?  Perhaps it's just better to lock it at release 12?  I'm not sure.  Thoughts?

Edit:  I went into Grub Customizer and simply unchecked the two entries for kernel release 13 and now Grub defaults to the previous version.  Problem solved for now :)

---

### Post by kio_http on 2011-12-07
> **diablo75 said:**
> Well I've made some discoveries and long story short I've narrowed down the cause of the problem to be Linux kernel version 3.0.0-13, which will lock the system (even if I select recovery mode for that version) if you use it.  However, version 3.0.0-12 works perfectly fine.

I figure the best work around for this would be to use [Grub Customizer]("https://launchpad.net/grub-customizer") to modify the default kernel selection so it will bypass the version that has the problem.  Perhaps there's a better work around?  Or maybe an even newer version of the kernel available I could try to install manually just to see if it solves the problem caused by release 13?  Perhaps it's just better to lock it at release 12?  I'm not sure.  Thoughts?

Edit:  I went into Grub Customizer and simply unchecked the two entries for kernel release 13 and now Grub defaults to the previous version.  Problem solved for now :)

Sounds like a driver issue. Did you ever use a binary nvidia driver from the nvidia.com site or something?

---

### Post by diablo75 on 2011-12-07
The nVidia driver that is in use is via the "Additional Drivers" applet but it doesn't give specific information about the version of driver that is in use and I don't know what command to enter into terminal to get that information.

I do have one additional bit of information to add.  The 13th release of the kernel no longer crashes when attempted to boot into it's recovery mode.  I've found that, for some reason, this is occurring thanks to a KVM switch I'm using between one monitor, another computer and this computer that I am trying to troubleshoot.  The KVM is an "iogear Model number GCS42UW6 serial Z39CT103AA70299".  I am still routing the video output through it but instead of attaching it's single USB port for the keyboard and mouse I am attaching a separate keyboard and mouse to the system.  Again, recovery mode for #13 now works as a result, but it still freezes during the bootsplash when attempting to boot normally.  This remains true even if there is no keyboard and mouse attached (I added #13 back into grub to experiment).

Perhaps it is a video driver issue but it doesn't not look like there is a better driver available via Jockey (See attached screenshot).

Here is the output of lspci to give you a little better view of the hardware makeup.

```

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

---

