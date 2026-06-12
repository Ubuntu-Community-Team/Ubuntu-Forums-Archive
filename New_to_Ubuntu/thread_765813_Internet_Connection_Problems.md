---
title: "Internet Connection Problems"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by chogoria on 2008-04-24
After successfully installing hardy, I can't get onto the internet. I could for a short while using a cable, then I went to adjust the wireless settings and then the wired connection stopped working. I've removed all of the changes I made as well as taking the cable out and putting it back in.

After a restart, I insert the network cable and it connects to the internet, I start firefox, it loads up the homepage and then stops working. All of the ip addresses etc are listed as 0.0.0.0.

ALSO (this has happened twice) once when using the live cd and the other time after a reboot, both of these times were when the internet was unavailable, I had a message at the top of the screen popping up telling me to update my wireless driver, but I couldn't due to no internet. How do I get this to pop up again when I have the internet?

Thanks in advance to your replies.

---

### Post by superprash2003 on 2008-04-24
have you enabled DHCP in your router.. and have you done the same in ubuntu network settings?

---

### Post by dokdoom on 2008-04-24
run 

ifconfig

eth0 should be running (sometimes it is default.)

then run

dhclient eth0 (or ethX where X = your interface you are running.)

---

### Post by chogoria on 2008-04-25
> **dokdoom said:**
> run 

ifconfig

eth0 should be running (sometimes it is default.)

then run

dhclient eth0 (or ethX where X = your interface you are running.)

OK i enabled DHCP as the post above you suggested and then ran your commands:

```

dan@dan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:69:aa:bd  
          inet6 addr: fe80::215:c5ff:fe69:aabd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5262 (5.1 KB)
          Interrupt:19 

eth0:avahi Link encap:Ethernet  HWaddr 00:15:c5:69:aa:bd  
          inet addr:169.254.9.52  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80742 (78.8 KB)  TX bytes:80742 (78.8 KB)

dan@dan-laptop:~$ dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
dan@dan-laptop:~$ 



```

---

### Post by superprash2003 on 2008-04-25
you dont seem to be getting an ip address inspite of enabling DHCP.. what is your router's ip address? try manually setting an ip

---

### Post by chogoria on 2008-04-25
> **superprash2003 said:**
> you dont seem to be getting an ip address inspite of enabling DHCP.. what is your router's ip address? try manually setting an ip

I've accessed my router by going to 192.168.1.254 (note I CANNOT do this in Ubuntu with my wired connection) It says I've got DHCP enabled.

Below where it tells me I have DHCP enabled it was a list of ip addresses: 
10.0.0.138/24       Static     (Edit Delete)
 
172.16.1.254/24     Static     (Edit Delete)
 
192.168.1.254/24    Static     (Edit Delete) 

None of these are the IP address I am connected to the internet as.

Please help, it's getting quite frustrating.

---

### Post by chogoria on 2008-04-25
PS. I'm using a BT Home Hub

---

### Post by chogoria on 2008-04-25
i've managed to get the wired connection running again by reseting the network settings using the command
```

sudo /etc/init.d/networking restart

```
For some unknown reason I dodn't try this before. Have also managed to install my wireless drivers due to me having access to the internet on my Ubuntu machine. However, after selecting my wireless network from the drop down menu and then entering my wireless key, only the bottom light on the connection status icon flashes and my router's wireless light dows not flash. Does this mean they're not interacting? 

Any ideas? Thanks in advance.

---

### Post by chogoria on 2008-04-25
Have been having a fiddle around a bit more trying to get things going with my wireless card...
Every time I restart Ubuntu and click on the network logo in the bar at the top right of the screen, underneath the "wireless networks" title there is nothing at all. If I then reload the "b43-fwcutter_011-1_i386.deb" file, the list of available networks appear when I click on the network icon at the top right of thescreen. I am able to enter the wireless key, but there is no further interaction between the computer and the router after this point. I have to reload the .deb file each time I load Ubuntu also.

Any ideas? Thanks.

I used the code
```

lspci -v

```

To find out what kind of network card I have. The output for the network controller section was:
```

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Dell Unknown device 0005
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]

```

---

### Post by chogoria on 2008-04-25
anyone have any ideas?

---

### Post by chogoria on 2008-04-26
/bump

---

