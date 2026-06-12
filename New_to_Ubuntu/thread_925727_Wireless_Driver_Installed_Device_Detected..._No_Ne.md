---
title: "Wireless Driver Installed Device Detected... No Network"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by atmu5fear on 2008-09-20
Hi, I have installed the Win XP drivers for my wireless card using ndiswrapper, and it shows the driver installed and device present, but in my task tray it won't let me enable wireless. I've tried sudo modprobe ndiswrapper to turn it on (it works on my laptop) but i don't get anything. Is there something i'm doing wrong?

---

### Post by atmu5fear on 2008-09-22
bump

---

### Post by Crafty Kisses on 2008-09-22
What type of wireless card do you have?

---

### Post by diablo75 on 2008-09-22
If this is on a laptop, you might check your BIOS settings to see if there are special hot-key functions that require you to hit something like FunctionKey-F4 (or something like that) to turn the adapter "on".  If that's the case, you should change the setting to make the card "Always On", or check to see if your laptop has a button/key combo/switch that needs to be toggled to enable the adapter.

---

### Post by willca on 2008-09-23
Hi

Ya know when my wifi nic goes acting up on me. I check if it even can see anything on the radar...

sudo iwlist wlan0 scan

This will tell me if its even on and if it can see a hotspot at all.

wlan0 because thats what I have, some have it as eth1.

If it does not show up anything or spits out an error saying no wireless network interface found or something...then likely the driver was not loaded right.

I would go to [www.ubuntuguide.org](www.ubuntuguide.org) and try the steps from there. The one that I like is from Feisty though I use Hardy. But they both work.

---

### Post by atmu5fear on 2008-09-23
Hey, no it's not a laptop, it's a desktop, so far getting wireless up on laptops has been gravy, but I can't get anything on my desktop. It's a D-Link DWA-542 n draft pci card. I've tried the XP, Win2000, and Vista 64 drivers. I can't get anything to register. In the terminal typing "ndiswrapper -l" gets me a 'driver installed, device present' message. When I run a hardware test from the admin menu, it lists my device as Atheros Communications Inc. AR5416 802.11abgn PCI Adapter (rev 01). Also listed is my wired ethernet controller, which is currently connected with 200ft of cable. My wired works, but in the task tray when left clicking the network icon it doesn't list wireless as an option, just wired. Right clicking the icon brings up the second menu with enable networking, but no enable wireless option. It's behaving as if there is no device or driver. Thanks for the help.

---

