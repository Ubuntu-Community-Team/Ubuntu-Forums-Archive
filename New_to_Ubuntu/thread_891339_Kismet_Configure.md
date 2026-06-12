---
title: "Kismet Configure"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-08-16
How do I configure the source= line in Kismet? (I am using wireless card WMP54g Linksys):

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,addme

I am trying to follow this tutorial:
[http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/)

---

### Post by hellodoggie on 2008-08-16
matthew@blackmagic:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"muckdo"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:24:60:F2:3D   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=55/100  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by hellodoggie on 2008-08-16
matthew@blackmagic:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)
05:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI
05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

---

### Post by cariboo on 2008-08-16
> #Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section

Have you made sure your wireless card is supported? The above mentioned readme file is probably located in /usr/share/doc/kismet

---

### Post by nicedude on 2008-08-16
Hello Doggie you have like 3+ threads all going here about WIFI cracking. I would suggest you read up on the subject using some nicely crafted google searches as it appears to me that you need to do some research, as there are so many questions that we all will not be able to answer them. Wifi cracking is not as simple as they say, If you have the right setup and know what to do then YES it is as easy as taking candy from a baby but if you know nothing and are new to linux then you should read up first then ask questions when you hit a brick wall not when you begin as that is what readme's are for. 

I will answer your question though as I am the nicedude, You need to install a Monitor mode capable driver and then you can use Kismet & Aircrack. Read the README for Kismet to see more.

---

