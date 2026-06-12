---
title: "New Ubuntu install, 2 problems"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by CB2RN on 2008-05-21
I know this is a repeat, but honestly I am more confused after searching for the answer than I was when I started. I have a Gateway M1625 Laptop. Currently, the webcam doesn't work and I'm not sure if the wireless works. Can someone walk me through setting them up?

For the cam, I tried to install easycam2, but the terminal can't find the package. Not sure what I'm doing wrong. I followed the instructions on the wiki. Also, how do I find out which webcam I have (the one installed from the manufacturer on the computer).

For the wireless, I have the Windows Wireless Drivers program, but I don't know where to get the right .inf file to install the driver.

Thanks
Don

---

### Post by Skeet on 2008-05-21
Do you know the brand of wireless card your laptop has? Often setting up wireless cards is specific to that model and has to be done in a certain way etc.

---

### Post by CB2RN on 2008-05-22
It is a Realtek wireless card. Not sure what brand the camera is.

---

### Post by starcannon on 2008-05-22
often times internal webcams are usb devices, that said, what does
```
lsusb
```
print out?

---

### Post by CB2RN on 2008-05-22
lsusb shows:

Bus 006 Device 006: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 006 Device 005: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 006 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 006 Device 003: ID 0c0b:5fab Dura Micro, Inc. (Acomdata) 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 001: ID 0000:0000


lshw -C network shows
*-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e7:6c:b6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=24.254.120.32 latency=0 module=r8169 multicast=yes


lspci shows:
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)


Honestly, I don't see the wireless card or the camera. Please point them out if you do.

---

### Post by starcannon on 2008-05-22
Your web cam is 
```
Bus 006 Device 006: ID 04f2:b027 Chicony Electronics Co., Ltd 
```

Your web cam is listed as supported and working drivers can be found here:
[Web Cam Drivers]("http://linux-uvc.berlios.de/")

While I don't see a recognizable wifi card, a little detective work let me know that the M1625 has a realtek b/g capable card, so I went to the realtek website and was able to narrow the possibilities down to 3, you can see them here:

[Realtek a/b/g/ wifi cards]("http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false")

So worst case scenario is you have to set it up 3 times to find the right one, that 8187b chipset is looking like its going to require ndiswrapper.

[SIZE="4"]**UPDATE**[/SIZE] It does look likely that your laptop has the rtl8187b as discussed in this article [http://forums.fedoraforum.org/forum/showthread.php?t=188020](http://forums.fedoraforum.org/forum/showthread.php?t=188020) *dang i'm good i should get a prize for that* :lol: okay but seriously, read that article it discusses the issue of it not showing up.

And then this link here:

[Ubuntu RTL8187b Guide]("http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/") 

shows how to install it using ndiswrapper in Ubuntu.

GL and hang in there, it looks like from what I've read that that is a sweet notebook, just need to do a little tweaking under Ubuntu's hood to get it there with Linux, but from the sounds of things it will be worth it, and it also sounds doable.

---

### Post by lswest on 2008-05-22
there is no wireless listed, are you sure it works? (in windows?) and make sure it's on when you boot the laptop.  Also, chicony is your web cam (mine works (chicony webcam) fine via cheese) ```
sudo apt-get install cheese
``` (needs internet)

---

### Post by CB2RN on 2008-05-22
Wow, thanks alot. I finally got the cam working through cheese. Haven't tried the wireless card yet, but it's much further along than I was. Thanks again.

---

### Post by lswest on 2008-05-22
no problem, glad it worked.  Thanks for the thanks :) and good luck with the wireless card.

---

### Post by starcannon on 2008-05-22
> **CB2RN said:**
> Wow, thanks alot. I finally got the cam working through cheese. Haven't tried the wireless card yet, but it's much further along than I was. Thanks again.

Glad to be of help, let us know how the wifi turns out.:KS

---

### Post by CB2RN on 2008-05-22
Well, I got the driver loaded, and nidswrapper -l shows:
net8187b : driver installed
	device (0BDA:8189) present
But nothing shows in the network panel. Do I have to turn it on somehow or mod something. I couldn't really follow the instructions on the Fedora forum, a little too technical.
Thanks

---

### Post by starcannon on 2008-05-22
[SIZE="4"]**UPDATE**[/SIZE]

I found a couple threads here at the forums, one of which is marked SOLVED
[8187b The Sovled Thread]("http://ubuntuforums.org/showthread.php?t=571046&highlight=Dougtron")

[Another 8187b thread]("http://ubuntuforums.org/showthread.php?t=765671&highlight=Dougtron")

[8187 Ubunt Hardy Guide]("http://mycirilo.com/?p=24")

GL I think with a bit of reading through these you should be able to get that thing connecting, let us know how it goes or how its going, I'll help where I can, mostly just good for research though.

~Starcannon

> **CB2RN said:**
> Well, I got the driver loaded, and nidswrapper -l shows:
net8187b : driver installed
	device (0BDA:8189) present
But nothing shows in the network panel. Do I have to turn it on somehow or mod something. I couldn't really follow the instructions on the Fedora forum, a little too technical.
Thanks

Look back at my previous post, theres a link there that is Ubuntu specific, I'll post it here again as well:

[Ubuntu rtl8187b NDISwrapper Guide]("http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/")

I'll do some more googling around for you, NDISwrapper is a pita, but its doable, just takes some work. Others have gotten this card up and working smoothly so its just a matter of finding the right solution for you.

---

### Post by CB2RN on 2008-05-22
Thanks again Starcannon. I followed the instructions on that particular link, and nothing. Still says driver installed, device detected, but doesn't show in the network.

---

### Post by CB2RN on 2008-05-22
iwconfig shows the following:
don@Dons-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I think this is the problem

---

### Post by starcannon on 2008-05-22
> **CB2RN said:**
> iwconfig shows the following:
don@Dons-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I think this is the problem

Look up a few posts, I put a bold update at the top of one with links to a solved thread and another guide.

---

### Post by stchman on 2008-05-22
If that wireless card gives you huge headaches then just go get a 3945abg wireless card.  They are around $20 and are very Linux friendly.

---

### Post by CB2RN on 2008-05-22
Well, I circumvented the problem. I got tired of fighting with it.
I went down to BestBuy and bought a Belkin F5D7050 USB adapter. It too took some work, but then it just magically worked. I'm not sure how. Not even sure if it will work tomorrow, but at least it will for now.

---

### Post by lswest on 2008-05-23
i just wanted to make sure you used to the step ```
sudo ndiswrapper -m
``` which should create the alias (wlan0) for your device.  If you did that step...not sure why it wasn't working.

---

### Post by CB2RN on 2008-05-23
I did use that step. Not sure why it's not working either, but now even the blue light on the laptop that shows the wireless is on refuses to come on. I think I turned the card off somehow. It works with the external adapter, so I'm good for now. Maybe I'll try again later.

---

### Post by Sbornaya on 2008-05-23
I only got my broadcom Wireless working with ndiswrapper once I had blacklisted the 43xx driver ubuntu attempted to use.
after blacklisted the modul ndiswrapper works perfect with the windows drivers.

just my2cts.

---

