---
title: "Wireless Networking Issue, cannot connect."
date: 2008-11-02
forum: New to Ubuntu
---

### Post by REIGN SS on 2008-11-02
I'm having an issue getting my wireless to work using Ubuntu 8.04. 

I'm Dual Booting 8.04/M$ Vista. I'm using a Netgear WG111v2 USB wireless adapter, I've tried using NDISwrapper with the appropriate driver but it still doesn't work.

From the searching I've done most people ask for the following commands:

**lspci:**
```
ryan@ryan:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
02:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)

```

**lsusb:**
```

ryan@ryan:~$ lsusb
Bus 002 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 002: ID 413c:5112 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 05dc:a450 Lexar Media, Inc. 
Bus 001 Device 006: ID 14cd:6600  
Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 001: ID 0000:0000  

```

**iwconfig:**
```
ryan@ryan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Obviously the wireless adapter works, as I am posting this from Windows Vista on the same computer. I'm still a n00b to Linux/Ubuntu but I'm up for some learning, so someone please take me to school.

Thanks in Advance,
Ryan

---

### Post by anewguy on 2008-11-02
I'm not familiar with your particular wireless, but I will note the following to you:

(1) As far as I know, you can't use the Vista drivers with ndiswrapper.  You need to use the Windows XP drivers.  This may have changed, but that's how it used to be.  I believe the driver also has to be a 32-bit version, not a 64-bit version.  Could be wrong -- but seem to remember this from reading some things on the forum a while back.

(2) I believe that there are "tricks" to getting ndiswrapper working if you are using 64-bit Ubuntu.  If you are, you may want to do a search in the forum for ndiswrapper and 64-bit.  I think it has something to do with using the 32-bit executable, but it's been a while since I read those threads.

May not be of much help to you, but wanted to be sure you research that to get the correct information and driver before you give up on ndiswrapper.

In addition, it seems many people have more luck using ndisgtk, the GUI'd front end to ndiswrapper.  You can install it via Synaptic.

Dave

---

### Post by REIGN SS on 2008-11-02
I do have the correct driver for my adapter, it's from Windows XP and I  did use the GUI interface to install the driver, and it accepted the driver and shows the device is connected to the computer.

---

### Post by REIGN SS on 2008-11-03
I Downloaded the i386 version of 8.04 and my wireless internet is working perfect now without NDISwrapper or anything... Guess it's a AMD64 issue :(

---

### Post by REIGN SS on 2008-11-03
OK... well it "worked" for about 3 minutes and now is back to not working at all! :(

---

### Post by MichaelSwengel on 2008-11-03
REIGN SS, 

Something you may want to consider is upgrading to 8.10 Intrepid. It has FAR better wireless support and may work better with your configuration.

You can upgrade with the Update Manager from Hardy. (Just make sure you have "Updates" set to "Normal"and not "Long Term Only" in the package manager)

All of your data will be preserved - so no worries there.

Intrepid fixed a lot of my problems, and it might for you. :)

---

### Post by REIGN SS on 2008-11-03
I upgraded, now I'm having a bit of a "different" issue.

[http://ubuntuforums.org/showthread.php?p=6093705#post6093705](http://ubuntuforums.org/showthread.php?p=6093705#post6093705)

---

### Post by anewguy on 2008-11-03
Sorry I couldn't have been of more help to you, but I'm glad you did get this working!

Dave :)

---

