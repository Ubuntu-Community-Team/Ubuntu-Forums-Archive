---
title: "connecting to the internet"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by mitar on 2008-05-20
I installed linux a month ago on my laptop while the school was still going on and in the dorm where I lived I only needed to plug internet cable to the wall and I would have internet connection. Everything was free and I did not need to use wireless (one of the reason is I can not get it to work, but that's not the problem now)

Now I got back home, and I can't just "plug the cable in the wall" so I need help about that. On a desktop PC we have adsl modem (I am really bad with terminology). (If you know what I am talking about) I was wandering if I could use that to have internet on my laptop. Do I have to set up something on laptop first or what (NOTE: I can not download anything from linux cause I'm not connected)
Second option would be to try to install dial up connection (the one that we used several years ago with speed of 52kbps ). But I don't think my laptop has modem iside

Can anyone help with this? I would provide any further information needed.

---

### Post by anfractuosities on 2008-05-20
run

 ifconfig 

in the terminal and post your results

applications > accessories > terminal

---

### Post by mitar on 2008-05-21
> **anfractuosities said:**
> run

 ifconfig 

in the terminal and post your results

applications > accessories > terminal

here:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:c6:ea:b1   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:220 Base address:0xa000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:10700 (10.4 KB)  TX bytes:10700 (10.4 KB) 

```

---

### Post by anfractuosities on 2008-05-22
Well if you have dsl at home you should be able to just plug it in to your computer.  If you want to use wireless, your home computer needs to have a wireless router.  

It seems to me that your wireless card is working properly, but just to make sure...in the menu go to

system > administration > network

is your wireless enabled?

---

### Post by mitar on 2008-05-22
I tried to use dsl, but it doesn't work. 

Since I switched to Linux I don't have wireless. I don't even have it as an option in system > administration > network. 
I looked other threads about wireless (because it seems that's common problem when you switch from windows) but non of them really helped. I don't know if you are familiar with HP laptops, they have a button switch that enables/disables wireless connection, but now it just doesn't work. But I never used wireless, so I really don't need it :-) I'll just wait until next semester when I go back to campus. The only solution would be if someone would look up my laptop (because I have no idea how all that stuff about internet works and how to set up connection), but I can't find any person who is familiar with Linux around me.

---

### Post by anfractuosities on 2008-05-22
what model is your laptop?  Did the wireless card come with it?  Do you know what the card is called?

---

### Post by Dissident85 on 2008-05-22
I had a similar problem. ummm post the output of

```
lspci
```

[http://ubuntuforums.org/showthread.php?t=791270](http://ubuntuforums.org/showthread.php?t=791270) <-- have a read through that thread as well, thats what helped me fix mine :)

---

### Post by mitar on 2008-05-23
> **Dissident85 said:**
> I had a similar problem. ummm post the output of

```
lspci
```

[http://ubuntuforums.org/showthread.php?t=791270](http://ubuntuforums.org/showthread.php?t=791270) <-- have a read through that thread as well, thats what helped me fix mine :)

here:

```
stefan@stefan-laptop:~$ lspci 
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
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03) 
stefan@stefan-laptop:~$  

```

---

### Post by mitar on 2008-05-23
> **anfractuosities said:**
> what model is your laptop?  Did the wireless card come with it?  Do you know what the card is called?

it's HP dv6000. Yes, wireless came. I had it when Vista was installed. I am not sure for the name, but I think this is it:

Broadcom Corporation BCM4328 802.11a/b/g/n

---

### Post by subzero316 on 2008-05-23
try,

```
sudo modprobe -r bcm43xx
```

---

### Post by mitar on 2008-05-23
> **subzero316 said:**
> try,

```
sudo modprobe -r bcm43xx
```

Nothing happened. It asked for password, and I entered but still nothing happened. I tried with full number (bcm4328 instead bcm43xx)
```
sudo modprobe -r bcm4328
FATAL: Module bcm4328 not found
```

---

### Post by subzero316 on 2008-05-23
ok then try with nidiswrapper

```
sudo aptitude install ndiswrapper-common
sudo aptitude install ndiswrapper-utils-1.9
sudo modprobe -r bcm43xx
sudo gedit /etc/modprobe.d/blacklist
```
In the end of the page append "blacklist bcm43xx" 
Get proprietary driver from the HP-site or dell site then copy the wifi driver files to a specific directory both .sys n .inf file
enter tat directory

```

sudo ndiswrapper -i bcmwl5.inf
```(bcmwl5.inf this is the name of the extracted inf file might differ)

```

sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper > /etc/module
```

---

### Post by mitar on 2008-05-23
ok, I downloaded driver but can you explain part "In the end of the page append "blacklist bcm43xx"
Get proprietary driver from the HP-site or dell site then copy the wifi driver files to a specific directory both .sys n .inf file
enter tat directory". I don't know what exactly I am supposed to do.

---

### Post by subzero316 on 2008-05-23
> ok, I downloaded driver but can you explain part "In the end of the page append "blacklist bcm43xx"

```
sudo gedit /etc/modprobe.d/blacklist
```
this command wud have opened a text editor,
in tat add the line in the end of the file

> Get proprietary driver from the HP-site or dell site then copy the wifi driver files to a specific directory both .sys n .inf file
enter tat directory". I don't know what exactly I am supposed to do.


1)Download the driver---u did it :KS
2)extract the files of the driver archive
3)i guess it will have all video driver, audio.......what we need is jus the wifi broadcomm so enter tat directory
4)in tat chk for the presence of .sys n .inf file which are the wifi driver files.(the bcm43XX.inf not sure abt the name sud be similar) be sure ur in this directory
5) type the remainig commands as in my previous post

---

### Post by mitar on 2008-05-23
> 2)extract the files of the driver archive

It came as .exe file. I only downloaded one driver (that I actually need). Can I somehow manipulate with .exe files in Linux???

---

### Post by subzero316 on 2008-05-23
must be a self extrator file...
with WINE it sud work. if u dont know much about wine then go to windows n do..Also try with 7zip i think it ll work have nvr tried...

---

### Post by mitar on 2008-05-23
Well, if you have no other sugestion, I guess my attempt to solve this problem ends here. I don't have wine and can't get it, because I don't have an internet. Installing files without internet is very hard (I've been trying to install inkscape since this morning and still can't get it to work, it always asks for some libpng, zlib, libgc,...)

One advice to you. When trying to help other you should type full words. Unless your keybord is missing certain letters. It's really hard to follow you when you type sud, n, ur,...

---

### Post by subzero316 on 2008-05-23
Yea sure...:)...no more chat words,

> Now I got back home, and I can't just "plug the cable in the wall" so I need help about that. On a desktop PC we have adsl modem 

first, Your driver for ethernet works fine so you can just plug in for your adsl connection. the only problem is network-manager is not present.
One thing you can do is if u have the ubuntu cd u can install network manager . or get WICD from internet and write it in a cd and install. make sure it is a debain package.


>  (If you know what I am talking about) I was wandering if I could use that to have internet on my laptop. Do I have to set up something on laptop first or what


where did you wander????:lolflag: use correct spelling

---

