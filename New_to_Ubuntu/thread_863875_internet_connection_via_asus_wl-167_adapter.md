---
title: "internet connection via asus wl-167 adapter"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by steveishere on 2008-07-18
Hi, I'm brand new to Ubuntu and am trying to get my asus wl-167 wireless USB network adapter to connect me to the Internet.  We have a in-house router through which we pick up broadband.

Amazingly, when I plugged the adapter into the USB port, Network Settings recognized it and started looking for local networks.  I was able to configure it using fixed DNS servers because I know the IP address for the router, as well as the WEP key.  Even more amazing, since I have access to page that shows the status of the wireless router, I was able to discover that the router shows my computer to be on the network.  

The problem is that I'm not connecting to the Internet. I'm connecting to the Internet now through my laptop, so our router Internet connection doesn't seem to be the issue.  What more do I need to do to get this to work?

---

### Post by phidia on 2008-07-19
Open a terminal window and put "iwconfig" (without the qoute marks) in there.
Copy and paste the output here.

---

### Post by steveishere on 2008-07-19
> **phidia said:**
> Open a terminal window and put "iwconfig" (without the qoute marks) in there.
Copy and paste the output here.

Sure, here you go.  Thanks! As you can probably guess, it's the wlan0 that has the adapter plugged in:


steve@steve-desktop:~$ iwconfig

lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"friends"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:D9:28:18   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=70/100  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.



steve@steve-desktop:~$

---

### Post by phidia on 2008-07-21
It is showing a connection that's for sure. Can you disable/open your security and try the connection with a browser-just to eliminate the problem being to do with security/passkey snafu?

There is also a [how to here]("http://ubuntuforums.org/showthread.php?t=684495") that can help with troubleshooting wireless.

---

### Post by steveishere on 2008-07-21
> **phidia said:**
> It is showing a connection that's for sure. Can you disable/open your security and try the connection with a browser-just to eliminate the problem being to do with security/passkey snafu?

There is also a [how to here]("http://ubuntuforums.org/showthread.php?t=684495") that can help with troubleshooting wireless.


Thanks, phidia!  

I can't disable the security on my router, unfortunately. I feel confident that I have the right WEP passcode, though,  Following the link you gave me I haven't had any more success, but maybe what I show here will tell you what's going on here:


steve@steve-desktop:~$ lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:55:d7:6b:ca
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.0.1 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:c6:18:66:f6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.1 multicast=yes wireless=IEEE 802.11g
steve@steve-desktop:~$ sudo ifconfig wlan0 down
[sudo] password for steve: 
steve@steve-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:55:d7:6b:ca  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61741 (60.2 KB)  TX bytes:61741 (60.2 KB)
steve@steve-desktop:~$ sudo ifconfig wlan0down
wlan0down: error fetching interface information: Device not found
steve@steve-desktop:~$ sudo ifconfig wlan0 down
steve@steve-desktop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:c6:18:66:f6
Sending on   LPF/wlan0/00:1f:c6:18:66:f6
Sending on   Socket/fallback
steve@steve-desktop:~$ sudo -f wlan0
sudo: illegal option `-f'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
steve@steve-desktop:~$ sudo -r wlan0
sudo: illegal option `-r'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
steve@steve-desktop:~$ sudo ifconfig wlan0 down
steve@steve-desktop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:c6:18:66:f6
Sending on   LPF/wlan0/00:1f:c6:18:66:f6
Sending on   Socket/fallback
steve@steve-desktop:~$ sudo ifconfig wlan0 192.168.0.1 netmask 255.255.255.0 up
steve@steve-desktop:~$ sudo route add default 192.168.0.1
SIOCADDRT: No such device
steve@steve-desktop:~$ sudo iwconfig wlan0 essid "friends"
steve@steve-desktop:~$ sudo iwconfig wlan0 mode Managed
steve@steve-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:c6:18:66:f6
Sending on   LPF/wlan0/00:1f:c6:18:66:f6
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.0.3 from 192.168.0.1
DHCPREQUEST of 192.168.0.3 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.3 from 192.168.0.1
SIOCADDRT: No such process
bound to 192.168.0.3 -- renewal in 34592 seconds.
steve@steve-desktop:~$

---

### Post by phidia on 2008-07-22
This line > SIOCADDRT: No such process looks like a problem. There are lots of hits from googling that including [this thread]("http://ubuntuforums.org/showthread.php?t=575512") at the ubuntu forums.

---

### Post by steveishere on 2008-07-22
> **phidia said:**
> This line  looks like a problem. There are lots of hits from googling that including [this thread]("http://ubuntuforums.org/showthread.php?t=575512") at the ubuntu forums.

IT WORKS, IT WORKS! 

Seriously, I was about to give up. I was considering reinstalling Windows and then saving up for a Mac (since I believe the writing is on the wall for Windows).  I am very much a newbie here, and while I've done a lot of things with Windows and even identified and isolated bugs in software, running commands in terminal mode (outside of directly copying what other people tell me to write) just seemed very much over my head, given that I didn't really know what I was typing or asking the machine to do.  

But I looked at the SIOCADDRT error and looked at where it occurred, and it occurred when it tried to connect with the IP address.  Someone at another forum had said that they did better when they did a direct connect with the IP address rather than go through DHCP Automatic Configuration. But if it wasn't connecting manually, then I thought that maybe DHCP would be best.  And so I did, and boom!  That did it.

This is huge.  I feel like I can fully use Ubuntu for the first time now.  Thanks so much!!!  :KS

---

