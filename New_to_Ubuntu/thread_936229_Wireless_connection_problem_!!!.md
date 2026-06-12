---
title: "Wireless connection problem !!!"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Christian91 on 2008-10-02
Hey guys,

I have just downloaded Ubuntu again after going away from it for a while and now I can't connect to wireless. I know there a lot of other threads about people who can't connect to their wireless, and I read them all but i still can't connect to my wireless. It doesn't show any wireless networks in the  top bar where you normally connect to them so i don't think my wireless card is installed? I don't know what the name of my card is.

Any help would be really helpful, thanks in advance :)

---

### Post by bobnutfield on 2008-10-02
Open a terminal and type:

> sudo lspci

Your network card should be shown close to the end of the list.

---

### Post by shifty_powers on 2008-10-02
can't wait for 8.10 to be released properly. been using kubuntu 8.10 for a while now and the wireless support is much better.

hopefully we'll see a lot less of these posts.

and yes, post the output of that and we'll try and help :D

---

### Post by bobnutfield on 2008-10-02
> **shifty_powers said:**
> can't wait for 8.10 to be released properly. been using kubuntu 8.10 for a while now and the wireless support is much better.

hopefully we'll see a lot less of these posts.

and yes, post the output of that and we'll try and help :D

I just installed Intrepid Beta today and I can confirm wireless support is better.  My demon RTL8187B is now supported natively.  No more ndiswrapper!

---

### Post by Christian91 on 2008-10-02
I'm so sorry, I know there are hundreds of others like this one :D hope you can help..

I get this:

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
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by bobnutfield on 2008-10-02
> 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01

Well, there it is.  There is a broadcom HOWTO on the forum.  I will find it and post the link back to you unless someone beats me to it.  I assume you are using Hardy.

EDIT:[http://ubuntuforums.org/showthread.php?t=870086&highlight=Broadcom+HOWTO]("http://ubuntuforums.org/showthread.php?t=870086&highlight=Broadcom+HOWTO")

Apprently, ndiswrapper is still the solution here, though I think the new Intrepid has support for it.  

EDIT:  In reading further, there should already be native support.

---

### Post by shifty_powers on 2008-10-02
[http://ubuntuforums.org/showthread.php?t=880218&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=880218&highlight=BCM4312)

follow the steps in that thread :D

---

### Post by Christian91 on 2008-10-02
Thanx a lot. yes, i use Hardy.

---

### Post by bobnutfield on 2008-10-02
The thread posted by shifty_powers is the one you should follow.  Sorry, the link I posted is a little out of date.

---

### Post by Christian91 on 2008-10-02
Well, it says that i have to create a blacklis file. and i have no idea what this is and make some contents to it in terminal? how do you do that ?

---

### Post by bobnutfield on 2008-10-02
The file that is being referred to is /etc/modprobe.d/blacklist.  If you following the instructions, you just add the module you want to black list by adding the following to the end of the above name file:

> blacklist <name of driver to blacklist

You open that file by typing in the terminal:

> sudo gedit /etc/modprobe.d/blacklist

Just add the above line to the end of the file and save.

---

