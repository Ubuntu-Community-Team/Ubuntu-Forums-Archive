---
title: "Ubuntu 8.10  64 bit AR5007 -No Internet Connectio using ath5k"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by lrigoulot on 2008-11-19
Hi,

Been working on this for days - I cannot connect to the internet after reading numerous .  HP dv9000 - I have a non secure network. I can't find the network manager even though synaptic says it is installed. Being a tolat N00b I did learn that the following might help:

louis@louis-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:3f:54:6e  
          inet addr:192.168.1.46  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe3f:546e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:746960 (746.9 KB)  TX bytes:61517 (61.5 KB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6428517 (6.4 MB)  TX bytes:6428517 (6.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:9a:74:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3A-9A-74-48-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

louis@louis-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Thanks in advance,
lou

---

### Post by pytheas22 on 2008-11-19
It looks like your wireless interface is up and active, so it should merely be a matter of telling it to connect.

The Network Manager icon is in the top-right corner of the screen (see screenshot).  It should look like two computer screens.  You have to *left*-click on it and it will display a list of wireless networks in range.

If for some strange reason Network Manager isn't loading (it should be there by default on Ubuntu 7.04 and later), you could use [wicd]("http://wicd.sourceforge.net") instead.

Also, if you post the output of the following command and tell us the name of your network, we can give you instructions for connecting manually:
```

sudo iwlist scan
```

---

### Post by lrigoulot on 2008-11-19
thanks but :

I have that same icon but it takes me to my wired connections

---

### Post by pytheas22 on 2008-11-19
In System>Administration>Network, do you have 'roaming mode' enabled?  If not, enable it.

Also, what is the output of:
```

sudo iwlist scan
```

---

### Post by lrigoulot on 2008-11-19
I have no system administration network - only network tool.

Here is the result:

louis@louis-laptop:~$ sudo iwlist scan
[sudo] password for louis: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:0E:44:BD:4E
                    ESSID:"dinger"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level:-29 dBm  Noise level=-101 dBm
                    Encryption key:off
                    IE: Unknown: 000664696E676572
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000026346cf6a
                    Extra: Last beacon: 540ms ago
          Cell 02 - Address: 46:00:E1:DC:10:CE
                    ESSID:"hpsetup"
                    Mode:Ad-Hoc
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/100  Signal level:-88 dBm  Noise level=-101 dBm
                    Encryption key:off
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: DD050010180100
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=00000050dedf7328
                    Extra: Last beacon: 536ms ago

pan0      Interface doesn't support scanning

thanks,
lou

---

### Post by pytheas22 on 2008-11-19
I don't know what's going on with Network Manager--it's very strange that it doesn't show you networks, because your card is definitely seeing them, as evidenced by the output in your last post.

If you run these commands, you should get connected:
```

sudo iwconfig wlan0 mode managed essid "dinger" channel 6
sudo dhclient wlan0
```

After the last command finishes running, you should be able to load web pages.

Once you're connected, I would recommend just downloading and installing [wicd]("http://wicd.sourceforge.net") by following the instructions on its site.  Then you will be able to connect in the future using the manager at Applications>Internet>WICD, instead of Network Manager.

---

### Post by lrigoulot on 2008-11-19
Still no luck, but thanks -

This is what I got:

louis@louis-laptop:~$ sudo iwconfig wlan0 mode managed essid "dinger" channel 6
[sudo] password for louis: 
louis@louis-laptop:~$ sudo iwconfig wlan0 mode managed essid "dinger" channel 6
louis@louis-laptop:~$ 
louis@louis-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3a:9a:74:48
Sending on   LPF/wlan0/00:1f:3a:9a:74:48
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
louis@louis-laptop:~$ 

Going to install wicd

---

### Post by lrigoulot on 2008-11-19
I added the following repositories:
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

found nothing and then tried:
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

still nothing so i removed it  --- strange

---

### Post by lrigoulot on 2008-11-19
got wicd - used Wicd by mistake

---

### Post by porchrat on 2008-11-19
please post the output of this:

```
lshw -C network
```

It will at least confirm that the driver is properly installed and being used.

---

### Post by lrigoulot on 2008-11-19
Did I tell you I love you? :lolflag:.

reboot and one click and I was on - I have disconnected my ethernet and this is done via wireless.  

Thank you again,

Lou

louis@louis-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:3f:54:6e
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:3a:9a:74:48
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.42 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:0d:46:34:50:36
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by porchrat on 2008-11-19
Awesome! Congratulations I hope you enjoy your wireless! :)

---

