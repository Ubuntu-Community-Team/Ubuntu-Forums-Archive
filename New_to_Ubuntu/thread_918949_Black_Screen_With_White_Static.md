---
title: "Black Screen With White Static"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by akamigs on 2008-09-13
Hey,

I'm somewhat new to linux. I installed XP and Ubuntu 8.04 on my Compaq Presario F730us notebook roughly four days ago.  

When I close my laptop and open it again, a black screen with white static lines appears, forcing me to shutdown the computer with the power button. When I shutdown the computer normally I get the same screen instead of the Ubuntu logo with the loading bar like I used to. The first few times after the installation everything was fine, which leads me to suspect that the problem was caused by one of system updates perhaps? I read somewhere that disabling the visual effects would fix the problem, but that didn't do anything. 

I've seen a lot of people use lspci when they need help. 
Hope this helps:

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
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
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
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

Thanks in advance.

---

### Post by skippuff54 on 2008-09-13
could be your video drivers, your refresh rate/screen res or maybe it's having trouble starting your GUI. or maybe the upgrade didn't work properly and you have conflicting drivers.

have u looked for solutions specific to that nvidia graphics card listed there, looks like a GeForce card?

do you remember what specific upgrades you applied? have you been doing any graphics related work or gaming? did you do the upgrades in synaptic?

---

### Post by akamigs on 2008-09-13
> **skippuff54 said:**
> 
have u looked for solutions specific to that nvidia graphics card listed there, looks like a GeForce card?

do you remember what specific upgrades you applied? have you been doing any graphics related work or gaming? did you do the upgrades in synaptic?

I have looked for solutions to my graphics card and have come up empty handed.

I simply did all of the updates that were recommended by the system. 

I have not done any graphics related work or gaming since I just installed it a few days ago. I'm still working on customizing it. I messed around with compiz-fusion a little bit, but I already disabled the visual effects and that didn't fix the problem. 

I did updates through the Synaptic Package Manager and the Update Manager. I THINK the screen began acting up after the Update Manager.

Thank you again.

---

### Post by skippuff54 on 2008-09-13
it sounds like somethin havin to do with your refresh rate, specifically when your OS tries to re-display your desktop as you open your screen.

can you go into system > admin > screen resolution and adjust the refresh rate? maybe decrease it?

i know nvidia can sometimes cause issues, look through the forums if u haven't already and make sure u have the proper nvidia drivers installed for the geforce card.

---

### Post by akamigs on 2008-09-13
> can you go into system > admin > screen resolution and adjust the refresh rate? maybe decrease it?

My initial screen resolution was 1280 x 800 with a refresh rate of 50hz.
I changed it to 800 x 600 with a refresh rate of 53hz and the problem continues to persist.

---

### Post by skippuff54 on 2008-09-13
i'd try bumpin it up to 60 or 75 mhz if possible. and i'd continue pokin around for solutions specific to that nvidia card listed when u did lspci.

---

### Post by panhandle on 2008-09-13
I have seen a few posts on this topic lately (Nvidia updates and problematic boot)...search these boards and you'll find others with similar problems.

See this link:

[http://ph.ubuntuforums.com/showthread.php?t=797270](http://ph.ubuntuforums.com/showthread.php?t=797270)

---

### Post by akamigs on 2008-09-13
> i'd try bumpin it up to 60 or 75 mhz if possible. and i'd continue pokin around for solutions specific to that nvidia card listed when u did lspci.

I can only bump it up to 56hz and still see everything on the screen. 

> 
I have seen a few posts on this topic lately (Nvidia updates and problematic boot)...search these boards and you'll find others with similar problems.

See this link:

[http://ph.ubuntuforums.com/showthread.php?t=797270](http://ph.ubuntuforums.com/showthread.php?t=797270)

I'll take a look right now, thanks.

---

