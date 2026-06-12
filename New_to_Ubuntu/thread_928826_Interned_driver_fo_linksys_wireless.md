---
title: "Interned driver fo linksys wireless"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-09-24
I have installed Ubuntu 7.10 on a HP Pavilon a 1610n desktop. This morning I found that I was able to connect to the internet via ethernet cable where I was not able to with wireless. When I checked the 'connection information' available, I noticed... Driver: forcedeth Is there a way of loading the correct driver to work with the Linksys wireless system ?

---

### Post by bobnutfield on 2008-09-24
Type 

> sudo lspci

so that we can see exactly what wireless card you have.  I assume this is an internal PCI card since it is a dekstop, but if it is a USB dongle, type:

> sudo lsusb

---

### Post by CoCoKnots on 2008-09-24
Thanks Bob, Here is what I came up with:

cole@captain-desktop:~$ sudo lspci
[sudo] password for cole:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem

cole@captain-desktop:~$ sudo lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 13b1:000d Linksys 
Bus 001 Device 001: ID 0000:0000  
cole@captain-desktop:~$ 

Hope this helps... Thanks

---

### Post by bobnutfield on 2008-09-24
That seems odd....it appears that both your wired and wireless interfaces are USB.  Is this correct?  Open a terminal and type:

> sudo ifconfig -a

and post the results.

---

### Post by CoCoKnots on 2008-09-24
Obviously, I have no idea what I am looking at...

Hope this helps.

cole@captain-desktop:~$ sudo ifconfig
[sudo] password for cole:
eth0      Link encap:Ethernet  HWaddr 00:18:F3:28:CA:37  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe28:ca37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2656989 (2.5 MB)  TX bytes:399112 (389.7 KB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:66:94:D1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163978 (160.1 KB)  TX bytes:3549 (3.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-66-94-D1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

cole@captain-desktop:~$

---

### Post by bobnutfield on 2008-09-24
OK, your wireless card is being recognized.  I am not sure what the results of having two interfaces up at the same time would be, so you may have to bring the wired connection down to get wireless.  But first, try this:

> sudo ifconfig wlan0 up
> sudo iwconfig wlan0 essid any
> sudo iwconfig wlan0 key <if you use encryption, type in here>
> sudo dhclient wlan0

Then, open System>Administration>Network and see if your wireless is shown as an opton.

---

### Post by CoCoKnots on 2008-09-24
Hey Bob, I tried this... It doesn't look correct. What should I have done ?


cole@captain-desktop:~$ sudo ifconfig wlan0 up
[sudo] password for cole:
cole@captain-desktop:~$ sudo iwconfig wlan0 essid any
cole@captain-desktop:~$ sudo iwconfig wlan0 key
Error for wireless request "Set Encode" (8B2A) :
    too few arguments.
cole@captain-desktop:~$ sudo iwconfig wan0 key 8B2A
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wan0 ; No such device.
cole@captain-desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:66:94:d1
Sending on   LPF/wlan0/00:12:17:66:94:d1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
cole@captain-desktop:~$

---

### Post by bobnutfield on 2008-09-24
Doesn't appear you are using encryption, so leave that be for the time being.  Did you check System>Administration>Network to see if the wireless is showing up there?  If it is, you may be able to set it up there.  Also try:

> sudo iwlist scan

to see if any networks show up.

---

### Post by CoCoKnots on 2008-09-24
Bob, I couldn't see anything when I went to System/Admin/Network...

Here is what I found when I typed the terminal command

cole@captain-desktop:~$ sudo iwlist scan
[sudo] password for cole:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:CE:47:56
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-25 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000052d3226d8c

cole@captain-desktop:~$

---

### Post by bobnutfield on 2008-09-24
Well, according to the scan, you ARE connected.  Now it is just a matter of getting an IP address.  It is possible to get two IP addresses using two ethernet cards (wired) but I do not know if the wired connection may be stopping you from getting an IP address from the wireless.  Try only these:

> sudo iwconfig essid linksys
> sudo dhclient wlan0

In the top corner of your panel, the network icon (little tv monitors) should be there.  Left click this and in the window, choose wlan0 from the drop down list.  See what results that yields.

---

### Post by CoCoKnots on 2008-09-24
Ok Bob, When I disconnect the Lan Cable to the Router I loose the internet connection. I also tried re-booting to see if it would find an address... No such luck. Here is the last commands you asked to see.

cole@captain-desktop:~$ sudo iwconfig essid linksys
[sudo] password for cole:
iwconfig: unknown command "linksys"

cole@captain-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6151
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:66:94:d1
Sending on   LPF/wlan0/00:12:17:66:94:d1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
cole@captain-desktop:~$

---

### Post by bobnutfield on 2008-09-24
Sorry, the first command should have said:  sudo iwconfig wlan0 essid linksys

Leaving out wlan0 is why it came back with an error.  Also, when you left click on the network icon in the top panel you should see the "linksys" network shown.  Click on that and see what happens.

---

### Post by CoCoKnots on 2008-09-24
Yes... Wired Network & Linksys are both listed... I ran the last corrected command you requested. Now do you need for me to disconnect the Lan Cable & try th wireless again ???  (Please excuse my typing. I keep hitting the wrong key).

---

### Post by bobnutfield on 2008-09-24
No, if the linksys is listed, just click on that and it should connect you by just changing netowrks.

---

### Post by CoCoKnots on 2008-09-24
I just tried that... The Linksys Wireless connection stalled & the system reverted back to the Wired connection.

---

### Post by bobnutfield on 2008-09-24
Well, I can only guess that means that it will not connect to both at the same time.  Type in a terminal:

> sudo ifconfig eth0 down

Then try to connect to the linksys again from the network icon.

---

### Post by CoCoKnots on 2008-09-24
Tried it... The search seized again... Rebooted system. Back on line (Wired Connection).

---

### Post by bobnutfield on 2008-09-24
Well, I have to admit I am stumped.  All the symptoms suggest you should be able to connect.  Hopefully, someone with experience with this type of problem will chime in.  You might also post a new thread in the Networking/Wireless forum about this specific issue.  There are a lot of wireless experts there.

---

### Post by CoCoKnots on 2008-09-24
Thanks for all the effort Bob. I do appreciate your time. I will take your advise & post on the Networking/Wireless forum.:)

---

### Post by bobnutfield on 2008-09-24
When you do post the new thread, reference this thread so you won't get people suggesting things you have already tried.  Best of luck with and I will bookmark this thread to see I can do a little research for you.

---

