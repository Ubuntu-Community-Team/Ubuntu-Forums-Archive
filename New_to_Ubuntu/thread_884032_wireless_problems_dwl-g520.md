---
title: "wireless problems dwl-g520"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by miningold on 2008-08-08
I know this is posted several places but i was unable to find anything that fit my situation.

My problem is i cannot access internet in ubuntu (8.04)

However, i did learn of what info to post:

**ifconfig:**
ath0      Link encap:Ethernet  HWaddr 00:13:46:6e:e9:87   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:14864 (14.5 KB) 
 
ath0:avahi Link encap:Ethernet  HWaddr 00:13:46:6e:e9:87   
          inet addr:169.254.8.49  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
 
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:49:6d:27   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:221 Base address:0x2000  
 
eth1      Link encap:Ethernet  HWaddr 00:1f:c6:49:74:91   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:222 Base address:0x6000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:3020 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3020 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:158512 (154.7 KB)  TX bytes:158512 (154.7 KB) 
 
wifi0     Link encap:UNSPEC  HWaddr 00-13-46-6E-E9-87-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:14518 errors:0 dropped:0 overruns:0 frame:7070 
          TX packets:4644 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199  
          RX bytes:1347082 (1.2 MB)  TX bytes:228084 (222.7 KB) 
          Interrupt:21 

**route -n**
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 ath0 
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 ath0 

**sudo lshw -C network**
 *-network                
       description: Wireless interface 
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor 
       vendor: Atheros Communications Inc. 
       physical id: 6 
       bus info: pci@0000:05:06.0 
       logical name: wifi0 
       version: 01 
       serial: 00:13:46:6e:e9:87 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

I DO NOT HAVE ACCESS TO INTERNET, i am using a separate computer to post this so i cant use apt-get or any of that stuff.

when i go to system>administrator>network, there is a wireless section and i can enter my passphrase but nothing happens

at system>administrator>network tools, ath0 is listed but i cant do anything with it.

Thank you for all your help, and once again in linux i have no access to the internet.

---

### Post by abyssius on 2008-08-08
The important information needed is what is the actual dwl520 model you are using? D-Link issued these cards with different chipsets. If you have the  D-Link System Inc DWL-520 Wireless PCI Adapter, Rev E1, then the only way it will work is to use the hostap utility. Here is a link to the instructions. 
  [https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1")

I'm using this card with no problems after following these instructions. Trying to use Ndiswrapper and the DWL520's windows driver will not work, so don't waste your time. I'm running Ubuntu 8.04.1 64-bit version. I hope this helps.

Oops, I just noticed that your version has the Atheros chipset. This is supposedly easier to set up. The recommended utility is:
[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi")

---

