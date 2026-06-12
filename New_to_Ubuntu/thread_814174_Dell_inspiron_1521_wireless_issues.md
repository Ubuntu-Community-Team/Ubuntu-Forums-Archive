---
title: "Dell inspiron 1521 wireless issues"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by MissMandie on 2008-05-31
Ok, first let me say that I am only about 7 hours into my first
Kubuntu install. I got fed up with Vista, completely wiped my hard drive of it and installed Kubuntu 7.10. (btw, let me say that I LOVE Kubuntu already and I love the idea of open source ware)I ran the restricted drivers and got the firmware for my Broadcom wireless card. It says it is installed. I have no problem getting on the internet with my ethernet cable but I have absolutely no luck with the wireless. Ive read a ton of posts but cant seem to find a fix. Im sure this is something silly I'm just overlooking. Any help would be greatly appreciated.

---

### Post by pytheas22 on 2008-05-31
Please post the output of these commands:

```
cat /etc/modprobe.d/blacklist
iwconfig
ifconfig
lspci
```

I suspect that you need to install the broadcom firmware.  These commands should give an idea of what's wrong.

---

### Post by MissMandie on 2008-05-31
missmandie@missmandie-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
missmandie@missmandie-laptop:~$



missmandie@missmandie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

missmandie@missmandie-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:**:**:**:07
          inet addr:***.***.*.** Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe89:5807/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:57553924 (54.8 MB)  TX bytes:1580730 (1.5 MB)
          Interrupt:21

eth1      Link encap:Ethernet  HWaddr 00:1C:26:1A:16:D8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3392 (3.3 KB)  TX bytes:546 (546.0 b)
          Interrupt:10

eth1:avah Link encap:Ethernet  HWaddr 00:1C:26:1A:16:D8
          inet addr:***.***.*.**  Bcast:169.***.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

missmandie@missmandie-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
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
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
missmandie@missmandie-laptop:~$                      


Hope you can make something out of this. Thanks!

---

### Post by pytheas22 on 2008-05-31
Hmmm, it appears from the output above that everything is installed correctly.  What happens when you try to connect?  Do either or both of the green dots on the Network Manager applet light up?

It would also be useful if you posted the output of:
```

iwlist eth1 scan
```

---

### Post by MissMandie on 2008-05-31
> missmandie@missmandie-laptop:~$ iwlist eth1 scan
eth1      No scan results


As far as the network manager, the last tab that says "network" is shaded out and I cant get to it. Could it have anything to do with this: when I go to system settings>network settings>network interfaces and click for admin privileges, I click on eth1 and configure interface, there is no ESSID or WEP key in those fields. What should those settings be?
Oh, when I try to log on using wireless or when I open the KWiFiManger, it says I have no signal strength but im sitting right next to my wireless router.

---

### Post by pytheas22 on 2008-06-01
There's something wrong if iwlist doesn't give any scan results--it means that the card is not seeing any networks.  Not having the Broadcom firmware installed could be the reason why (for legal reasons, Ubuntu can't include this, and the restricted drivers thing may not have downloaded it correctly).  Try running this command:
```

sudo apt-get install bcm43xx-fwcutter
```

you will be asked at one point if the firmware should be fetched automatically; say yes.  When it's done, reboot the computer and see if the wireless works.

If it still doesn't work, there are more things to try, but hopefully the firmware was the problem.

---

### Post by MissMandie on 2008-06-01
Heres what I got. 

> missmandie@missmandie-laptop:~$ sudo apt-get install bcm43xx-fwcutter
[sudo] password for missmandie:
Reading package lists... Done
Building dependency tree
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 177 not upgraded.
missmandie@missmandie-laptop:~$


Not too promising. Should I go ahead and try the ndiswrapper thing I've read so much about? I was trying to avoid it 'cause it sounds pretty complicated and im a complete noob.

---

### Post by pytheas22 on 2008-06-01
That's what I was afraid of.  Just to be sure that the firmware is already installed, what is the output of:

```
ls /lib/firmware
```

If that directory isn't empty, then yeah, I guess ndiswrapper is the only way to go, unless anyone else has any idea why this wouldn't be working.  I'm stumped, because everything looks like it should be ok based on the output you've given.

Ndiswrapper's actually not that hard as long as you don't run into any weird problems, and if you install the ndiswrapper-gtk utility, you don't even need to use the command-line to set it up.  There's a guide [here]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)") specific to your card; if you run into trouble, feel free to post.

---

### Post by MissMandie on 2008-06-01
Here's what that code gave me. 
> missmandie@missmandie-laptop:~$ ls /lib/firmware
2.6.22-14-generic  bcm43xx_microcode11.fw

Guess im going to go ahead and try ndiswrapper. keep your fingers crossed!

---

### Post by MissMandie on 2008-06-01
Still no luck. Its getting really confusing and frustrating. Not sure where to go from here.

---

### Post by pytheas22 on 2008-06-01
Did you follow that tutorial?

Also try running this command and reboot and see if it helps:
```

sudo -s
echo 'blacklist bcm43xx' >> /etc/modprobe.d/blacklist
exit
```

If it still doesn't work after rebooting, post the output of:
```

iwconfig
ifconfig
ndiswrapper -l
```

---

### Post by gmstalk on 2008-06-03
I have a Dell Inspiron 1521 and I had to use ndniswrapper to get my wireless to work. There are several posts on this. You will need the XP version of the bcmwl5 driver. You can download it from Dell.

---

### Post by MissMandie on 2008-08-16
0K, I've decided to get rid of everything I've done so far and start over. I just don't know where to start. I checked all the outputs of the command lines we went through before and several of them have changed. Don't know if that is good or bad. I do know that I have a broadcom bcm4312 802.11 modem. I downloaded the driver from the broadcom website but I don't know how to get it working. I've rebooted several times but still no luck. Here are my new outputs:> missmandie@missmandie-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx
missmandie@missmandie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

missmandie@missmandie-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:89:58:07
          inet addr:192.168.1.93  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe89:5807/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:797 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1290739 (1.2 MB)  TX bytes:147178 (143.7 KB)
          Interrupt:21

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

missmandie@missmandie-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
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
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
missmandie@missmandie-laptop:~$ iwlist eth scan
eth       Interface doesn't support scanning.

missmandie@missmandie-laptop:~$ ls /lib/firmware
2.6.22-14-generic  bcm43xx_microcode11.fw
missmandie@missmandie-laptop:~$


---

### Post by pytheas22 on 2008-08-16
Broadcom recently released native Linux drivers (which is a huge deal in light of Broadcom's anti-Linux policies in the past) and they purport to support 4312 cards.  [This thread]("http://ubuntuforums.org/showthread.php?t=880218") has instructions for easily installing them.  I'd give them a try first, and please report back (it would also be good to report your results either way in that thread, in order to help the Ubuntu developers).  If they don't help you, we can try again using the reverse-engineered drivers (i.e., not the ones being given out by Broadcom).

---

### Post by alexis777 on 2008-11-27
Hi, MissMandy, Did you finally make your wireless to work? I have a Inspiron 1521 too, I put Debian Etch on it, but now I'm thinking on uninstall it, because I just can't make the wireless work. I'been reading around that it works fine on Ubuntu, so I downloaded Kubuntu 8.1, to try it on, but now that I find your threat, I'm getting a little nervous. And want to ask you too: Are your Laptop's speakers working on Ubuntu? because that's another issue that I haven't been able to fix on etch. Thanks in advance for your answers.

---

### Post by pytheas22 on 2008-11-28
alexis777: I don't know if MissMandy will answer, but if not, if you post the output of the following commands, I'll try to help you with the wireless (I'm afraid I don't know too much about your sound problems):
```

lspci -nn
lsusb
lshw -C Network
uname -m
```

Also, what do you currently have installed--Debian Etch or Kubuntu 8.10?

---

### Post by alexis777 on 2008-11-29
This is the output of the commands you ask me for:

lspci -nn

00:00.0 Host bridge [0600]: ATI Technologies Inc Unknown device [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7915]
00:07.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SB600 SMBus [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SB600 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SB600 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:791f]
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832] (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)

lsusb

Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 0000:0000  

lshw -C Network (I didn't know about this one)

  *-network UNCLAIMED
       description: Network controller
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:fe8fc000-fe8fffff irq:10
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:1d:09:b1:a6:f5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half ip=201.248.19.127 latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:fe5fe000-fe5fffff irq:201
  *-network
       description: IEEE1394 interface
       physical id: 2
       logical name: eth0
       serial: 35:4f:c0:00:3c:51
       capabilities: ieee1394 physical
       configuration: broadcast=yes driver=eth1394 multicast=yes

uname -m

x86_64

I used the b43-fwcutter to download the firmware, but didn't work, then I read in the berlios web page that due to my kernel version I should use bc43xx-fwcutter to use the legacy firmware, so I try that package but the repositories for etch (and as I read also for lenny) are broken. I didn't even try the nspluginwrapper stuff because as people say around (the web), probably I would end on the same place, but with a mess of wierd packages on the system. I still have etch, and I downloaded the iso for Kubuntu 8.10 to put it over etch, thinking that it would easier my life.

I appreciate any word of wisdom on this.

---

### Post by pytheas22 on 2008-12-01
Thanks for that information.  You have a Broadcom 94311 card, which can be a bit tricky but is really not as bad as it used to be.  I think that if you upgraded to Ubuntu 8.10 (possibly 8.04 as well), your card would work, using b43-fwcutter, simply by going to System>Hardware Drivers and enabling it.  But on Debian Etch, maybe the kernel is too old; I don't know.  Older builds of the b43 driver won't support this card, which is probably your problem.  Which kernel are you using?

In any case, you can use ndiswrapper.  If you run these commands, they should get you up and running, at least on Ubuntu--I can't guarantee that they'll work on Debian as well, but they might.  This is copied and pasted from the [ndiswrapper Broadcom guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").

```
echo -e 'blacklist bcm43xx\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Then reboot.  If you think that everything above worked as planned but you still don't have wireless after rebooting, please post the output of:
```

lshw -C Network
dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

---

### Post by RavUn on 2008-12-01
For most of the broadcom drivers, the issue was fixed in an update of 8.04.  It didn't work with the initial installation but after upgrading it worked fine.  Installing 8.10 should include what you need... but I don't know if it covers the 1390 card.  There was a sticky in the networking and wireless thread but it looks like it's been removed since most of the issues were resolved with the updates.

---

### Post by alexis777 on 2008-12-01
I installed Kubuntu 8.10 and everything works fine. First, I try the live cd feature, and the wlan device was detected, but didn't connect because of the lack of the firmware. Then I installed the distribution on the hard drive, installed bcm43xx-fwcutter, and the wlan interface was detected right away, and the signals appeared on the network manager.  Although the signal is presented by the network manager slightly diminish (about 70 to 85%) the connection is working fine, without dropping, and I'm getting the same max speed that I got on Vista. I'm using WPA on my router, and is supported too.

By the way, the issues with the sound are fixed in the alsa version that comes with the distro. And the Radeon Xpress is also supported, at least for 2D. I will try to compile the acceleration support later.

I don't remember exactly, but I think Etch use the 2.6.18 kernel.

thanks for your comments.

---

