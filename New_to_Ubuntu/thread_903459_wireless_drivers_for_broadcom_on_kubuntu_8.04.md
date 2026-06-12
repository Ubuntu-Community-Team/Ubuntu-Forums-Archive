---
title: "wireless drivers for broadcom on kubuntu 8.04????"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-08-28
i can install build essentials or fw cutter how do i get my drivers to work? im afraid the interface with kde is substantially more complex than gnome

---

### Post by ladr0n on 2008-08-28
> **PatrickMoore said:**
> im afraid the interface with kde is substantially more complex than gnome
What do you mean?  Any good tutorial should be giving you the command-line way to solve the problem, which should be exactly the same for all variants of Ubuntu.

I have a "Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)", and I've found the best way to get it to work is to use ndiswrapper (there are several good tutorials for that on these forums).  What is the output of the command 'lspci | grep Broadcom'?

---

### Post by PatrickMoore on 2008-08-28
> **ladr0n said:**
> What do you mean?  Any good tutorial should be giving you the command-line way to solve the problem, which should be exactly the same for all variants of Ubuntu.

I have a "Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)", and I've found the best way to get it to work is to use ndiswrapper (there are several good tutorials for that on these forums).  What is the output of the command 'lspci | grep Broadcom'?

my only issue with kubuntu so far has been that i dont appear to have a package installer. i just found ubuntu easier in that sense.  i just started playing with kubuntu so it was an initial reaction. and to clarify i CANNOT install my fwcutter file or Build Essentials

---

### Post by PatrickMoore on 2008-08-28
wow where did all my response go?

i just started playing with kubuntu so it was an initial reaction. i dont like that i cannot instal packages as easy as i did with ubuntu.  but im probably missing some cool program that helps me

---

### Post by PatrickMoore on 2008-08-28
> **ladr0n said:**
> What do you mean?  Any good tutorial should be giving you the command-line way to solve the problem, which should be exactly the same for all variants of Ubuntu.

I have a "Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)", and I've found the best way to get it to work is to use ndiswrapper (there are several good tutorials for that on these forums).  What is the output of the command 'lspci | grep Broadcom'?

lspci | grep Broadcom: yields nothing

---

### Post by arochester on 2008-08-28
If lspci | grep Broadcom yields nothing, what is the output of just > lspci ???

---

### Post by PatrickMoore on 2008-08-28
> **arochester said:**
> If lspci | grep Broadcom yields nothing, what is the output of just  ???

bear with me im using two computers

---

### Post by PatrickMoore on 2008-08-28
> **PatrickMoore said:**
> bear with me im using two computers

```
i
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
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAMController
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

---

### Post by PatrickMoore on 2008-08-28
> **PatrickMoore said:**
> ```
i
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
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAMController
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

i think that is complete

---

### Post by PatrickMoore on 2008-08-28
anyone got anything?

---

### Post by PatrickMoore on 2008-08-28
i really need help with this seeing that this is a different circumstance than when i installed ubuntu

---

### Post by vikram on 2008-08-28
If it helps I am using a different broadcom based wireless adapter(BCM4312)  - it works fine with ndiswrapper. have you tried that ?

---

### Post by PatrickMoore on 2008-08-28
> **vikram said:**
> If it helps I am using a different broadcom based wireless adapter(BCM4312)  - it works fine with ndiswrapper. have you tried that ?

no ive actually never used ndiswrapper

---

### Post by vikram on 2008-08-28
please see 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
note: you can use adept (System > Adept) to install packages in Kubuntu

Once you have your driver set up for Kubuntu I would recommend KNetworkManager to search for wireless networks and enter passwords etc.
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)

---

### Post by PatrickMoore on 2008-08-28
i found a page devoted to this but i dont have an internet connecion (im using my girlfriendscomputer for that)
 so i need help with other options (live cd?)

---

### Post by vikram on 2008-08-29
One option is to goto the ndiswrapper site, copy the latest source onto a USB disk and compile it. Otherwise I usually use the ethernet port to connect via a wire to download stuff to set up wireless

---

