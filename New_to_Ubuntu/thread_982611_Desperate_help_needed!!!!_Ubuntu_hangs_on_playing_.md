---
title: "Desperate help needed!!!! Ubuntu hangs on playing video!!!!!"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by bobigeorge on 2008-11-14
Hello friends,

I am using Ubuntu in my HP lap for almost 3 years and satisfied with its performance. 

I propagate Ubuntu among my friends at my college also.

I have installed Ubuntu 8.04 in COMPAQ PRESARIO V3000 lap of one of my interested friends.

But every time when he plays a video the whole system hangs. :-(

I have tried VLC, Real Player, Mplayer, and default movie player...

Result of ```
lspci
``` is
```

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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
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
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```


Somebody pls help me....

It is a matter of prestige as I boast about Ubuntu a lot before my loyal M$ Windows users... 

Otherwise it will be an embarrassment both for me and Ubuntu..

---

### Post by jimmy the saint on 2008-11-14
What video driver are you using?  if you installed the restricted driver, try to disable it and see if it solves your problem. If you are not, try to use it and see if THAT solves your problem.

---

### Post by Mardoct909 on 2008-11-14
As good a reason as any for wanting help.

Did you try setting the output mode to X11?

Try disabling desktop effects (if enabled)?

Is it fully updated?

---

### Post by bobigeorge on 2008-11-14
Thank you for the quick help..

Desktop effects are disabled and it is fully updated...

Plz tell me some more about how to set output mode to x11..

---

### Post by bobigeorge on 2008-11-14
Thank you jimmy the saint,

I have tried your solution earlier. But no result...

---

### Post by Mardoct909 on 2008-11-14
Setting it to X11... Umm... I don't know. I never had to do it. I just saw it work for someone else in a similar circumstance somewhere else. Try scouring the menus of the player. I'm sure it is possible with VLC, though. Try that one first.

---

### Post by jimmy the saint on 2008-11-14
X11 would be in video options.  Have you tried playing different videos?  Different types of videos? (MPEG, AVI, WMV etc)  Maybe it is a codec issue.

Worst case, maybe the video card is buggy.  if it is using on board decoders maybe they are fryed?  Im kind of shooting in the dark here so I'm going to stop.  But brainstorms can be helpful (except when they aren't)

---

### Post by Mardoct909 on 2008-11-14
Is this computer old or abused? That would certainly increase the chance of hardware failure.

If all else fails, tell them that Google and IBM seem to think Linux is better.

---

### Post by bobigeorge on 2008-11-15
No... it's a brand new lap top.. 

He was running Windows smoothly(:-()

---

### Post by 3rdalbum on 2008-11-15
> **bobigeorge said:**
> No... it's a brand new lap top.. 


With a GeForce 6150?

I'm running Ubuntu 8.10 which has a completely different version of VLC, but here's the directions to change the video output module:

1. Go into the VLC preferences (Tools > Preferences in 8.10)
2. Click Video in the left pane; I think there's a little triangle next to it that allows you to open out more settings.
3. In the bottom-right of the window is a checkbox for "Show Advanced Settings". Tick that.
4. Somewhere in the "Video" section of the preferences is a popup menu for "Video Output Module". You can change this to XVideo, X11, or OpenGL output. X11 seems to be the more reliable on Nvidia cards.

---

