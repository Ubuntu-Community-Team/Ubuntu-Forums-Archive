---
title: "[SOLVED] Linksys WUSB54G v.4/Ubuntu 8.04/Dell Inspiron2650"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by SMU4US on 2008-11-25
Unable to get Linksys WUSB54G v.4 to work on Dell Inspiron 2650 with Ubuntu 8.04.  Using the Ndiswrapper tool, it worked initially but painfully slow (i.e. 2-3 minutes to open a link or timed out.  

The following morning and since then, it does not appear to connect to my wireless network and I changed nothing.  Many posts seem to indicate problems with Ndiswrapper and maybe I need to another solution?

Is getting this adapter to work simply beyond absolute beginner level and should I look for a card that is more compatible with Ubuntu 8.04?  

The wireless network to which I want to connect is named Dillo.  My WRT54GS v.6 router has the Dillo network configured with WPA Personal Security.  Even when it 'sees” ESSID:Dillo , I have not been able to connect to the Internet since the first night. Unable to determine what conditions allow it to “recognize” ESSID:Dillo.  Clearly when it does not, I am not getting any IP address assigned.  The inconsistency is maddening and I am out of ideas.

Without understanding fully what these command lines do, I am posting the following as suggested:

$lscpi
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)

02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller


$ifconfig     (with no wired connection)
eth0      Link encap:Ethernet  HWaddr 00:06:5b:b9:2c:fb  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:10 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2082 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2082 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:104748 (102.2 KB)  TX bytes:104748 (102.2 KB)



wlan0     Link encap:Ethernet  HWaddr 00:14:bf:74:c2:ff  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wlan0:avahi Link encap:Ethernet  HWaddr 00:14:bf:74:c2:ff  

          inet addr:169.254.10.242  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1



wmaster0  Link encap:UNSPEC  HWaddr 00-14-BF-74-C2-FF-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
$iwconfig gives different results at different times.

 Sometimes iwconfig yields:

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:"Dillo"  

          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:70:87:A4:47   

          Bit Rate=1 Mb/s   Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Link Quality=43/100  Signal level=-47 dBm  

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Other times  iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:""  

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated     
PROBLEM Here?
          Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ifconfig wlan0
$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
$ sudo lshw -C network

[sudo] password for rwagoner: 

  *-network               

       description: Ethernet interface

       product: 3c905C-TX/TX-M [Tornado]

       vendor: 3Com Corporation

       physical id: 1

       bus info: pci@0000:02:01.0

       logical name: eth0

       version: 78

       serial: 00:06:5b:b9:2c:fb

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=80 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s

  *-network

       description: Wireless interface

       physical id: 2

       logical name: wlan0

       serial: 00:14:bf:74:c2:ff

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


$ iwlist scan 
lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wmaster0  Interface doesn't support scanning.



wlan0     No scan result


$ sudo /etc/init.d/networking restart
sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 5565

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



wmaster0: unknown hardware address type 801

wmaster0: unknown hardware address type 801

Listening on LPF/wlan0/00:14:bf:74:c2:ff

Sending on   LPF/wlan0/00:14:bf:74:c2:ff

Sending on   Socket/fallback

DHCPRELEASE on wlan0 to 192.168.1.1 port 67

There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



wmaster0: unknown hardware address type 801

wmaster0: unknown hardware address type 801

Listening on LPF/wlan0/00:14:bf:74:c2:ff

Sending on   LPF/wlan0/00:14:bf:74:c2:ff

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

Help!

---

### Post by snowpine on 2008-11-25
Hi there, I have the exact same device (Linksys WUSB54Gv4) and it gave me a headache when I first started using Linux! Fortunately, I found these instructions: [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

That worked for me. It sounds from your description like you did not blacklist the module. 

Hope that helps!

---

### Post by SMU4US on 2008-11-25
Unsure hot RT2500 referred to in your link relates to me?  Also I am trying to understand your comment about Black List.  Please explain.  I have only been trying Ubuntu for about 1 month.

---

### Post by snowpine on 2008-11-25
Hi there, I had exactly the same confusion as you when I started in Ubuntu, so don't feel bad. :) I wish I was a wireless expert and could explain it better. Unfortunately the best I can do is give you a link to a tutorial that worked for me. I carefully followed the steps in post #1 of the thread I linked to, and it worked.

My understanding of what that tutorial teaches is this: Linux includes a rt2500usb driver (which theoretically is what we need to get the WUSB54gv4 to work). However, it doesn't work (as you discovered). So, we need to "blacklist" rt2500usb to stop Linux from using its own version. Instead, we install ndiswrapper, an application that allows us to use Windows drivers. Then, we can download the working Windows driver from the Linksys website and use that instead of the Linux version. The thread I linked to really explains it better than I can myself. :)

---

### Post by SMU4US on 2008-11-26
> **snowpine said:**
> Hi there, I had exactly the same confusion as you when I started in Ubuntu, so don't feel bad. :) I wish I was a wireless expert and could explain it better. Unfortunately the best I can do is give you a link to a tutorial that worked for me. I carefully followed the steps in post #1 of the thread I linked to, and it worked.

My understanding of what that tutorial teaches is this: Linux includes a rt2500usb driver (which theoretically is what we need to get the WUSB54gv4 to work). However, it doesn't work (as you discovered). So, we need to "blacklist" rt2500usb to stop Linux from using its own version. Instead, we install ndiswrapper, an application that allows us to use Windows drivers. Then, we can download the working Windows driver from the Linksys website and use that instead of the Linux version. The thread I linked to really explains it better than I can myself. :)
Great explanation, Snowpine.  Now the rt2500 part is making sense.  Thanks for that.  I have downloaded the Windows driver and thought through the tutorial which is more clear now.

Now, since I initially installed (what was apparently the rt2500usb) driver using the Ndiswrapper tool, do I need to uninstall that somehow uninstall that?

---

### Post by trellis2 on 2008-12-24
I have had the linksys wusb54g working on a Dell 530S using 8.10 intrepid. Had to install with wireless linksys usb54g plugged in. After install usb54g device was detected and worked.

have also blacklisted rt2500 and that worked. But I had to put in a loooooootta time and research into it. Given the choice autodetect under 8.10 was easier. I'll look to see if I can find the articles.

---

### Post by SMU4US on 2008-12-31
> **trellis2 said:**
> I have had the linksys wusb54g working on a Dell 530S using 8.10 intrepid. Had to install with wireless linksys usb54g plugged in. After install usb54g device was detected and worked.

have also blacklisted rt2500 and that worked. But I had to put in a loooooootta time and research into it. Given the choice autodetect under 8.10 was easier. I'll look to see if I can find the articles.
Thank you, Trellis2.  I am still struggling with this problem.  If you do find the article you mentioned, I would definitely appreciate.

---

