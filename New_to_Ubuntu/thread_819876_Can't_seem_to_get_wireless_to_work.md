---
title: "Can't seem to get wireless to work"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by MixedMadness on 2008-06-05
Hello all, I'm running Ubuntu Studio 8.04 on a Lenovo ideapad y510 with Intel PRO/wireless 4965AGN integrated wireless card, and I can't seem to get the wireless internet to work.  From what I can tell, and I am a complete noob, the system seems to recognize that there is a wireless interface available.  I just can't get it to see my wireless network.  I'm used to seeing a list of available networks to connect to, and though I've done it once, I can't seem to remember how to list available networks in the terminal.

So, here's what I've got so far:

ifconfig:
```
joe@UbuntuStudio1:~$ sudo ifconfig
[sudo] password for joe: 
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:7b:52:e8  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe7b:52e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2988 (2.9 KB)  TX bytes:8569 (8.3 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75800 (74.0 KB)  TX bytes:75800 (74.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:7e:72:e3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1d:e0:7e:72:e3  
          inet addr:169.254.9.143  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-7E-72-E3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

iwconfig:
```
joe@UbuntuStudio1:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"jojonetwork"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:6174-6C70-696D-7031-3939-39
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


lspci:
```
joe@UbuntuStudio1:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:03.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

Also, I'm on cat5 so I can browse the web (and get help), should I try searching for available networks with it unplugged?  (how do I search for available networks?)  Oh, and the wireless switch is in the ON position.  And please feel free to explain what all that junk I posted means (I know, sort of).

I would really REALLY appreciate any help.  Thanks in advance.

Peace,
Joe

---

### Post by jbrown96 on 2008-06-07
ifconfig simply lists all the network interfaces that are currently up. eth0 is your cat5/ethernet card. You can see that it has an ip address listed; that's really the only important part. lo is the internal loopback address. I'm not completely sure about what it does, but I believe that it's used if a program has to communicate with itself/other programs on the same machine. wlan0 is your wireless card. The others are new and they have to do with the recent change from ipw* to iwl* drivers. They don't do anything, so disregard them. 
iwconfig shows specific wireless related info. It looks like your computer is trying to connect to "jojonetwork". That may be your problem. 
lspci lists the detected hardware on the machine. 
You don't need to use sudo for most commands just to see the state. lspci and iwconfig should not be run with sudo. If you are doing something in any of the commands (ex. bringing an interface up/down with ifconfig, changing wireless modes with iwconfig) then sudo is needed.

```
iwlist scan
``` will search for networks. See if that returns anything. If it does, your computer seems to be stuck in a custom/manual mode. I'm assuming you haven't done anything too exotic. Try left clicking on your network icon --> manual configuration --> make sure that "roaming mode" is enable for your wireless device. 
If that doesn't work, it's worth trying to connect without network-manager. There must be a better way to do this, but I can't think of it. Go into system monitor (System-->Administration) Under processes, find "nm-applet" and kill it. Back to the command line. An unsecured network would be best to try this on (I'm not sure about the usage with encrypted networks). ```
sudo iwconfig wlan0 essid "NETWORK NAME"
``` obviously replace "NETWORK NAME" with the desired network. Give minute to connect and ```
iwconfig
``` If that shows the network name in ESSID then you're set. Confirm with ```
ifconfig wlan0
``` to verify that you are getting a ip address. 

hopefully something in there helps you.

---

### Post by ConMan318 on 2008-06-07
I was going through the same thing as you a while back, and I tried connecting via command line for a week or so with little luck.  On these forums, someone recommended that I install wicd (it's like network manager but better (imho)).

Since you said that your card is recognized, it should be as easy as entering the wireless password and clicking connect, like it was for me.  Unless you have a specific reason to connect via command line, or you are in love with network manager (installing wicd will delete it), I'd say to give it a shot.

It's not in the default repos, to add it you'll have to go in Synaptic to settings > repositories > 3rd party software > add and type in:
```

deb http://apt.wicd.net **hardy** extras

```

If you are using gutsy, replace hardy with gutsy obviously.

---

