---
title: "WLAN problems on Fujitsu Siemens"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by saikas on 2008-05-12
Hi, I just installed Ubuntu on my laptop. Looks like everything works fine except my WLAN card. Here is 3 buttons which dont work without drivers. One of that buttons turns on/off WLAN card... and i have drivers only for win xp. Maybe some one tried Ubuntu on Amilo A1645G. And successfully bypassed this problem?

---

### Post by lswest on 2008-05-12
can you post back the output of ```
lshw -C network
lspci
``` 1 line= 1 command, and you have to run it in the terminal (applications-->accessories-->terminal)  just copy (right-click and choose "copy" or <shift>+<ctrl>+<c>) and paste (right-click and paste, or <ctrl>+<v>) the output into a text document and stick it on a USB stick if you don't have any internet on the laptop atm.

---

### Post by saikas on 2008-05-12
Ok, wheb i get home i try to connect cabel and write that line:)

p.s. i know how to copy:) i'm now only on linux, but not on pc's:)
thanks for helping me

---

### Post by lswest on 2008-05-12
> **saikas said:**
> Ok, wheb i get home i try to connect cabel and write that line:)

p.s. i know how to copy:) i'm now only on linux, but not on pc's:)
thanks for helping me

i actually added that in because ctrl+c doesn't copy in a terminal, it's shift+ctrl+c for copying and so i decided i'd add the rest in so that people realize to paste into a text doc it's not shift+ctrl+v, but ctrl+v like people expect.  Not implying you needed to know it, or that you didn't know it, just wanted to make it as clear as possible.

---

### Post by saikas on 2008-05-12
> **lswest said:**
> can you post back the output of ```
lshw -C network
lspci
``` 1 line= 1 command, and you have to run it in the terminal (applications-->accessories-->terminal)  just copy (right-click and choose "copy" or <shift>+<ctrl>+<c>) and paste (right-click and paste, or <ctrl>+<v>) the output into a text document and stick it on a USB stick if you don't have any internet on the laptop atm.

well i hope i copied everything u need for some solution:)

 *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: wifi0
       version: 01
       serial: 00:02:e3:47:ac:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:af:8c:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
saigunas@saigunas-laptop:~$ 
saigunas@saigunas-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
02:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
saigunas@saigunas-laptop:~$

---

### Post by lswest on 2008-05-12
Well, i've personally never owned an atheros card, but i saw this thread: [http://ubuntuforums.org/showthread.php?t=748004](http://ubuntuforums.org/showthread.php?t=748004) and thought it might be useful for you to have a look at that first.  Did you install any kind of drivers?  if not, you can look at madwifi, or install the windows drivers via ndiswrapper for the wireless card (i believe)

---

### Post by saikas on 2008-05-12
> **lswest said:**
> Well, i've personally never owned an atheros card, but i saw this thread: [http://ubuntuforums.org/showthread.php?t=748004](http://ubuntuforums.org/showthread.php?t=748004) and thought it might be useful for you to have a look at that first.  Did you install any kind of drivers?  if not, you can look at madwifi, or install the windows drivers via ndiswrapper for the wireless card (i believe)

I see, but i think biggest problem is not my wifi card, but in quick lounch buttons which should turn on/off it. in windows while launch manager is not installed wifi also don't work. maybe u know command to run this program "launchmanager_v1_3_4_wxp.exe" on linux???

beside how install drivers on linux? i also need to instal ati grafic card.

---

### Post by NIT006.5 on 2008-05-14
saikas for the moment I think you should ignore the quick launch buttons you're referring to. Just because it worked like that on Windows doesn't necessarily mean it will operate the same on Ubuntu/Linux (particularly if those buttons are software controlled). Concentrate first on trying to get the driver for the wireless card installed and if you still have issues after that, then worry about the buttons.

So,

Check under Network Properties to make sure that no wireless connection is shown.

Check under System->Administration->Hardware Drivers (on Hardy) OR System->Administration->Restricted Drivers (on Gutsy). Check if there are any drivers listed there that need to be enabled. If there is, enable it and then check in Network Settings again to see if a wireless connection is shown. 

If no drivers were listed, then:

(a) Download and install ndisgtk. (This depends on ndiswrapper and ndis-utils so they should be installed automatically with ndisgtk). These packages will allow you to install the Windows driver that came with your card. They can be intalled via System->Administration->Synaptic Package Manager (in Synaptic, search for 'ndis'). 

(b) Once those are installed, you should be able to install the Windows driver via System->Administration->Windows Wireless Drivers. (Just click 'Add' and browse to the INF file of the Windows driver).

Check again under System->Administration->Network to see if a wireless connection is shown. If a connection is shown, then the drivers are fine and it should just be configuration. If there is still no network connection shown, then the drivers are either not installed or are not the correct drivers.

If you have definitely got EITHER the Linux driver OR the Windows driver installed (via ndiswrapper), and if it's still not working, then you can look deeper at the button issue.

---

### Post by saikas on 2008-05-16
Hey,

Well I did what u said, but still nothig, so now i try to run madwifi..
but do not know how to run it:(
I don't know any linux code:(

---

### Post by NIT006.5 on 2008-05-16
> **saikas said:**
> Hey,

Well I did what u said, but still nothig, so now i try to run madwifi..
but do not know how to run it:(
I don't know any linux code:(

Hi,

When you say "nothing", do you mean there is no wireless connection showing up in network settings, or that it's there but it's not working? Can you be more specific.

Which points exactly did you try? Did you succeed in installing ndiswrapper? Did you succeed in installing the windows drivers? Does it show the hardware as being present in ndisgtk (Windows Wireless Drivers)? Can you be more specific about what happened at each point.

---

### Post by saikas on 2008-05-17
hey,
finaly i'm online:)don't realy knw how, but i did it with help from you. i tried windows drivers and than madwifi. and now it works, little bit sloly and unstabile, but still better then nothing:)
so thanks

---

### Post by saikas on 2008-05-17
> **saikas said:**
> hey,
finaly i'm online:)don't realy knw how, but i did it with help from you. i tried windows drivers and than madwifi. and now it works, little bit sloly and unstabile, but still better then nothing:)
so thanks

grrr:confused:i don't understand ubuntu. i just restarted pc afer installing video drivers and now wireless is gone.:confused:even card is gone:confused::confused::confused:

---

### Post by NIT006.5 on 2008-05-19
> **saikas said:**
> grrr:confused:i don't understand ubuntu. i just restarted pc afer installing video drivers and now wireless is gone.:confused:even card is gone:confused::confused::confused:

What version of Ubuntu are you running? I have seen problems on Gutsy (7.10) where Windows drivers would have to be re-installed after each boot, but this problem seems to be fixed in Hardy (8.04). As a quick pointer, if the connection isn't shown in Network Settings, then it usually means its a problem with drivers.

---

### Post by iklein on 2008-07-04
Hi,

I have just the same trouble on Fujitsu-Siemens Li2727 and I'm gonna tired of Ubuntu!
I need for Launch Manager such in Windows that makes active Fn+F1 to turn on the WLAN-card on somehow to do this in terminal!!!
I installed Atheros driver via ndiswrapper, set roaming mode and then nothing.

Help, please!

P.S. Only the trouble with WLAN is prevent me to use Ubuntu completely. 'Cause I'm not going to buy a new device!

---

### Post by NIT006.5 on 2008-07-07
Which version of Ubuntu are you running? I haven't had any issues at all since I upgraded to Hardy. And I think there have also been some updates to wireless on Hardy since it was released. So make sure that the system is 100% up-to-date before looking at any other solutions. If it's already up-to-date, then I don't have any ideas.

---

### Post by adebax on 2008-11-10
Hey all you ubuntix,

I realized the dates of this thread, but for I found it while researching the problem myself, my answer might still be helpfull to some people. The problem of the FS Notebooks working with Launch Manager Buttons is quite easy to solve: 
Go to BIOS and [enhance] the WIRELESS option. 
That should it be -even without using the terminal ;-) 

Good luck!

---

