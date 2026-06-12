---
title: "Yet Another Atheros Wifi Problem (YAAWP)"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Spoodt on 2008-08-01
Right now I am running Xubuntu, however this same probelm was encountered under Ubuntu, and I belive it to be unaffected by distro. While following the basic Madwifi install, I hit a dead end at the step where you create your wireless interface. What shuold come up after typing in iwconfig is this:

"Now, if you type iwconfig, you should see a list like the following:

eth0      no wireless extensions.

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Then we need to bring up the wireless interface. This is done by typing (as root):

ifconfig ath0 up

There is more information on the creating of interfaces in UserDocs."

However, when I type iwconfig, only see eth0 and lo. ath0 and wifi0 don't even exist. I know I followed every step correctly, I've compared multiple guides, and I've searched the net for an answer with no luck. Please, overlook my n00bn355 and help a brother out. =/

---

### Post by phidia on 2008-08-01
What specific wireless card and version of X/Ubuntu are you using?
And actually "iwconfig" should show a wlan0 for a wireless card-well normally.
Can you post the output of "lshw -C network"?

---

### Post by Spoodt on 2008-08-01
Its an atheros arr5007 I think, and my laptop is a Compaq f700. There are a couple of issues regarding installing drivers on this laptop that I've encountered on fourums, but not this one. And this is Xubuntu 8.04. 

I am fairly new to this, so i could be at fault here, but the output for your command was. bash: Ishw: command not found. Sry o.o

---

### Post by dca on 2008-08-01
With Atheros/madwifi it shows up as ath0 w/ Wifi0 as your loopback or something there-abouts...

---

### Post by dca on 2008-08-01
> **Spoodt said:**
> Its an atheros arr5007 I think, and my laptop is a Compaq f700. There are a couple of issues regarding installing drivers on this laptop that I've encountered on fourums, but not this one. And this is Xubuntu 8.04. 

I am fairly new to this, so i could be at fault here, but the output for your command was. bash: Ishw: command not found. Sry o.o

If it was that card (Windows = AR5006, Linux 2.6.18 > = AR5007, Linux 2.6.23 > = AR242x) it wouldn't have an ath0 listed w/ info in it.
 
Try 'lspci' at command line and post it here.

---

### Post by Spoodt on 2008-08-01
oxide@oxide-laptop:~/madwifi-hal-0.10.5.6-r3835-20080801$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
oxide@oxide-laptop:~/madwifi-hal-0.10.5.6-r3835-20080801$

---

### Post by dca on 2008-08-01
RATS!  It is the one we're talking about.

---

### Post by Spoodt on 2008-08-01
SOLVED IT! Apparently, making a wireless interface isn't needed. All tht has to be done is restarting after $sudo modprobe ath_pci (or was it pci_ath?)

Anyways, someone should put this on Madwifi's Installation Guide. Thanks for the help Penguin and Mel Gibson!

---

### Post by dca on 2008-08-01
This is how I got it to work in Ubuntu GNOME version
 
[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)

---

### Post by dca on 2008-08-01
> **Spoodt said:**
> SOLVED IT! Apparently, making a wireless interface isn't needed. All tht has to be done is restarting after $sudo modprobe ath_pci (or was it pci_ath?)

Anyways, someone should put this on Madwifi's Installation Guide. Thanks for the help Penguin and Mel Gibson!

Excellent!  I just found the post I used to get it working in Ubuntu 7.x! 
 
You're absolutely correct, you have to add the module to the running kernel using the 'modprobe ath_pci' command...  Sometimes you need to reboot, sometimes not...

---

