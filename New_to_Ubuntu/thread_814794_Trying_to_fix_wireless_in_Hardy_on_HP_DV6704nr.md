---
title: "Trying to fix wireless in Hardy on HP DV6704nr"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by paraplegicpanda on 2008-06-01
Okay, I have been through a multitude of posts and have been utterly unsuccessful. I had my wireless card working in Gutsy, then I made the mistake of upgrading to Hardy. After it broke everything in my OS (even video and wireless), I backed up all my files and did a clean install of Hardy. Now I have virtually everything working great except for the wireless, I tried my method of getting the wireless to work with madwifi drivers in Gutsy and it didn't work. I have gotten ndiswrapper to work (sort of...).

lspci:
```
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
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

When I open open Wicd I can see networks and even attempt to connect, but it is never successful. The only error I actually see is when I open up my Network Settings, everything is grayed out.

I couldn't get it to work when I first got ndiswrapper going, but then I restarted the computer and was able to connect to my girlfriend's wireless router with WEP. I haven't been able to connect to any routers, regardless of security, including my girlfriend's. Anybody have any ideas?


HP DV6704NR
Ubuntu 8.04 Hardy Heron 64-bit
AMD 64 Athlon X2

---

### Post by StaceyRVC on 2008-06-01
is this a broadcom modem?
if so, have you tried this thread [http://ubuntuforums.org/showthread.php?t=765448](http://ubuntuforums.org/showthread.php?t=765448)

---

### Post by sam_delta on 2008-06-01
> **StaceyRVC said:**
> is this a broadcom modem?
if so, have you tried this thread [http://ubuntuforums.org/showthread.php?t=765448](http://ubuntuforums.org/showthread.php?t=765448)

check out his lspci output:

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

sam

---

### Post by StaceyRVC on 2008-06-01
> **sam_delta said:**
> check out his lspci output:

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

sam
sorry i read too quickly and jumped to my issues that i had with the broadcom... I apologize for being a noob

---

### Post by paraplegicpanda on 2008-06-01
Thanks Sam and don't worry Stacey, it happens... I'm pretty sure it's an Atheros ar5007eg. I have three different possible ndiswrapper drivers that I am trying out right now to see if that fixes my problem, but I'm still looking for answers so any help is appreciated!!!

---

### Post by paraplegicpanda on 2008-06-01
New ndiswrapper drivers didn't work... still looking for help...

---

### Post by paraplegicpanda on 2008-06-01
Also, I am getting a message when I pull up my ndiswrapper that says "Unable to see if hardware is present."

---

### Post by sam_delta on 2008-06-01
> **StaceyRVC said:**
> sorry i read too quickly and jumped to my issues that i had with the broadcom... I apologize for being a noob

hey stacey, dont worry, it happens to all of us, really dont worry

now, about the wireless, you should use your windows xp drivers for ndiswrapper, few questions

do you have wired connection? 


try searching into system>administration>Hardware Drivers, and check if there are any wireless driver listed (check this while connected to a wired connection, cuz it downloads it from ubuntu servers), if not

have you tried the latest madwifi?, some sites/posts suggest madwifi for your card, if so, how did you installed them?

finally if no drivers are listed under hardware drivers and wifi does not work, i can help you on installing ndiswrapper

sam

---

### Post by paraplegicpanda on 2008-06-01
I have already removed all of the wireless problems from the Restricted Drivers... From what I have read MadWifi drivers will work on 32-bit but not 64-bit yet.

---

### Post by sam_delta on 2008-06-01
EDIT-- not so sure about this info anymore, thats why i deleted it
i duno much about 64 bit since i dont have one but
ur using ndiswrapper for 64bit?
sam

---

### Post by Unix_Slayer on 2008-06-01
I had the same problem. The 32bit drivers work. In some cases the 64bit doesn't.

---

### Post by paraplegicpanda on 2008-06-01
Yeah, I have three versions of the driver, all from Acer, but the latest one should be working... 

ndiswrapper -l
```
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

```

Also, ath_pci is blacklisted. And I am using 64 bit drivers.

---

### Post by paraplegicpanda on 2008-06-01
Okay, so I am posting from my wireless connection right now. Here's what I did to finally get it working...

I installed ndiswrapper.
I installed the latest 64 bit version of the windows driver for my wireless card. (Available on my web server [here]("http://trezy.com/64bit_athdriver_v5-3-0-67.zip").)
I also turned off the wireless security on my router. I am not sure if it was just my router or something else... I will post again once I can verify access through security.

---

### Post by paraplegicpanda on 2008-06-01
Success!!! I switched from WICD back to Network Manager and I have been successful connecting to my secured wireless network!!! Woohoo!!!

*edit* I can only connect to WPA networks, not WEP... Any ideas?

---

### Post by Unix_Slayer on 2008-06-01
> **paraplegicpanda said:**
> Success!!! I switched from WICD back to Network Manager and I have been successful connecting to my secured wireless network!!! Woohoo!!!

*edit* I can only connect to WPA networks, not WEP... Any ideas?


WPA or WPA2 are actually more secure then Wep. I wouldn't complain about that one. Congrats.

---

### Post by paraplegicpanda on 2008-06-01
I wouldn't complain but I use WEP in a few different places... Also, I think it may have something to do with the driver because everytime I try to connect to a WEP network, I have to reinstall the driver...

---

### Post by sam_delta on 2008-06-01
glad its working

enjoy ubuntu :)

sam

---

### Post by paraplegicpanda on 2008-06-01
Okay, so my ndiswrapper will work for a little while, then I have to uninstall the driver from ndiswrapper and reinstall it. Anybody have any ideas? I couldn't find anything about it online.

---

### Post by Unix_Slayer on 2008-06-01
> **paraplegicpanda said:**
> Okay, so my ndiswrapper will work for a little while, then I have to uninstall the driver from ndiswrapper and reinstall it. Anybody have any ideas? I couldn't find anything about it online.


It's the 64 bit driver. I told you it's not working up to par. Try the 32 bit one. I had the same problem with the 64 bit.

---

### Post by paraplegicpanda on 2008-06-02
I attempted the 32-bit drivers and they didn't work. I would rather be restricted to just wired networks than switch back to 32-bit Ubuntu... I have had a bit more success so far with keeping the wireless working... I have gone most of the day and it is still working. I'll update either when it goes out again or if it makes it all the way to Tuesday.

---

### Post by Unix_Slayer on 2008-06-02
> **paraplegicpanda said:**
> I attempted the 32-bit drivers and they didn't work. I would rather be restricted to just wired networks than switch back to 32-bit Ubuntu... I have had a bit more success so far with keeping the wireless working... I have gone most of the day and it is still working. I'll update either when it goes out again or if it makes it all the way to Tuesday.


That's weird. I'm using 64 bit Kubuntu, and the 32 bit driver works. Maybe the Win2000 .inf will work. I know the Vista .inf's don't work for sure.

---

### Post by paraplegicpanda on 2008-06-04
Yeah, I'm using ndiswrapper for my 64 bit install. I have just kind of given in to the reinstallation method... I just reinstall the driver every so often and everything is gravy.

---

### Post by Unix_Slayer on 2008-06-04
> **paraplegicpanda said:**
> Yeah, I'm using ndiswrapper for my 64 bit install. I have just kind of given in to the reinstallation method... I just reinstall the driver every so often and everything is gravy.

If it's every time you boot, sounds like a write access restriction on one of the hardware configuration files.

---

### Post by paraplegicpanda on 2008-06-05
It's not necessarily every time I boot... Sometimes I can boot three or four times without problems...

---

### Post by Unix_Slayer on 2008-06-05
> **paraplegicpanda said:**
> It's not necessarily every time I boot... Sometimes I can boot three or four times without problems...


Yeah but doesn't it make you wonder why.

---

### Post by paraplegicpanda on 2008-06-05
Yes, it makes me horribly curious but I can't figure it out. I figure I'll just wait for the next release of the madwifi drivers and hope they work for me...

---

### Post by KinderX on 2008-11-28
kim having this problem as well

---

### Post by paraplegicpanda on 2008-11-28
I actually diagnosed my problem... My laptop has started overheating recently and everytime I ctrl+alt+backspace, it overheats, or the desktop environment drops out for whatever reason I have to reload the driver in ndiswrapper. I will eventually write a script to fix it so I don't have to mess with it anymore, but for the time being I have just made the driver files easily accessible and I remove and reinstall the driver everytime I need to. I'm more than happy to help fellow users out with this though, so email me at [email]paraplegicpanda@gmail.com[/email] if you need help.


P.S. - No I don't care about putting my email in an open forum.

---

