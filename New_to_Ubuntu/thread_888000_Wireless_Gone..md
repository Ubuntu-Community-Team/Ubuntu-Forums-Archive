---
title: "Wireless Gone."
date: 2008-08-12
forum: New to Ubuntu
---

### Post by KaiXXV on 2008-08-12
Alright, I don't know if anyone else has had this problem, but I booted up my laptop this morning and Ubuntu (8.04) no longer detects my laptop as having the proper drivers (or any) for my WiFi (Internal) card.  I'm currently running on an HP DV6000t. (I think it's *t*) I've followed several of the guides that are posted and have yet to find a solution that works.  I'm willing to post any information needed.

P.S. I forgot to mention I'm on a fresh install now.  (Thought maybe re-doing everything would fix it.)

---

### Post by nicedude on 2008-08-12
From that model # I think you should have a Intel PRO/Wireless 3945 802.11 a/b/g wifi adapter, I believe this is Broadcom chipset based. I don't have or use any of the Broadcom chipset wifi adapters so I can't tell you how to fix it, but you should read up on that chipset model here in the forums as there are guides on how to use it. Why it would break all of a sudden is a mystery though , but most likely due to either a system update that broke something or you changing something the broke it so any info as to when or how this happened and anything you just installed would help. So would the output of "iwconfig" as well as "lspci" commands.

Hope this helps you get on the right track to figuring it out.

---

### Post by KaiXXV on 2008-08-12
LSPCI
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

IWCONFIG
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by djh2008 on 2008-08-12
I have this same problem.

I have a Portege R200, and was running Ubuntu 7.10 and wireless worked okay with a drop down menu of the available wireless networks in range.
I updated to 8.04 and this has gone and the system network manager appears greyed out?

Any help much appreciated. I've tried searching these forums but to be honest I don't know how to apply some of the console/kernal fixes or scripts.

Thanks.

---

### Post by nicedude on 2008-08-12
OK guys here is a link to a thread on your adapter that is marked as SOLVED so it should contain instructions on how to fix your problem. To the guy who started this thread your adapters driver just isn't installed which is why it doesn't show up in iwconfig, just go to the following thread and read through it till you see the solution. If you need help with anything in particular that they tell you to do then you can PM me and I will try to instruct you.

[http://ubuntuforums.org/showthread.php?t=820297&highlight=Intel+PRO%2FWireless+3945](http://ubuntuforums.org/showthread.php?t=820297&highlight=Intel+PRO%2FWireless+3945)

Good luck guys with your wifi

nicedude

---

### Post by KaiXXV on 2008-08-14
Alright, well, I tried there method and yet I have nothing.  Any other things you'd think might work?  Maybe downgrading to a previous version of Ubuntu?

---

