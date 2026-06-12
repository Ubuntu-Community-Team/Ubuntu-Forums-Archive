---
title: "No Internet, Need Help"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by piperdown10 on 2008-05-09
I'm trying to install a PCI wired ethernet card and can't get it to work. I've looked on the disk and there are drivers for Linux but the instructions appears to be for RedHat only.

It's showing up under 'lspci' as: 02:0a.0 Ethernet controller: AMDtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

It's a Linksys 10/100 EtherFast PCI Adapter. An info you need, let me know and I'll get it to you asap.

Thanks,
pd

---

### Post by prshah on 2008-05-09
> **piperdown10 said:**
> 
It's showing up under 'lspci' as: 02:0a.0 Ethernet controller: AMDtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)


Output of ```
ifconfig
```, and more details please on your setup.

---

### Post by piperdown10 on 2008-05-09
I'm running Hardy, just finished installing it actually. I have 1.7 GB with 768 MB of RAM and a 40GB HDD.

Here's the output:
eth0      Link encap:Ethernet  HWaddr 00:1a:70:13:27:33  
          inet6 addr: fe80::21a:70ff:fe13:2733/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:1 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:314412 (307.0 KB)  TX bytes:6723 (6.5 KB)
          Interrupt:16 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57412 (56.0 KB)  TX bytes:57412 (56.0 KB)

---

### Post by prshah on 2008-05-09
> **piperdown10 said:**
> I'm running Hardy, just finished installing it actually. I have 1.7 GB with 768 MB of RAM and a 40GB HDD.

Here's the output:
eth0      Link encap:Ethernet  HWaddr 00:1a:70:13:27:33  
[color=red]          inet6 addr: fe80::21a:70ff:fe13:2733/64 Scope:Link[/color]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:1 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:314412 (307.0 KB)  TX bytes:6723 (6.5 KB)
          Interrupt:16 Base address:0xe800 


Looks fine; but you may want to disable ipv6 by adding ```
blacklist ipv6
``` to your /etc/modprobe.d/blacklist; unless you are using it.

I need more information on how you connect to the Internet... do you use a adsl router? In which case, what does ```
sudo dhclient eth0
``` give you?

---

### Post by piperdown10 on 2008-05-09
I went in and edited the blacklist and added ipv6.

Here's the output of duso dhclient eth0:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:70:13:27:33
Sending on   LPF/eth0/00:1a:70:13:27:33
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by kevinatkins on 2008-05-09
Hi,

That looks to me like your router's DHCP server isn't running.. Under normal circumstances, the default on many routers is to enable DHCP but it's possible I suppose that it's been turned off. What make / model router are you using? You can often reset routers to factory defaults by pressing and holding a reset button with a paperclip, but be aware that if you do that, you might need to reconfigure any internet connection (eg, ADSL).

---

### Post by piperdown10 on 2008-05-09
I'm directly wired into my cable modem. I tried enabling a DHCP connection and still no internet.

---

### Post by kevinatkins on 2008-05-09
OK. Do you have access to another machine by any chance, or a means of perhaps booting into Windows? Or do you know the exact IP address of the router?

---

### Post by prshah on 2008-05-09
> **piperdown10 said:**
> I'm directly wired into my cable modem. I tried enabling a DHCP connection and still no internet.

As previous poster said; DHCP not working; you can try till you're blue in the face, it won't work.

That said, in _Windows_, can you post the output of ```
ipconfig /all
``` that will give us the details of the IP setup, and we can use this information to enable your Internet in ubuntu.

---

### Post by piperdown10 on 2008-05-09
I'm on another machine now. Unfortunately, I don't know the IP Address.

---

### Post by piperdown10 on 2008-05-09
This is the ifconfig for the machine that I'm on:

eth0      Link encap:Ethernet  HWaddr 00:02:3F:38:72:07  
          inet addr:68.53.50.145  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::202:3fff:fe38:7207/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21473219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:539981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2447701766 (2.2 GB)  TX bytes:54713269 (52.1 MB)
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1488 (1.4 KB)  TX bytes:1488 (1.4 KB)

---

### Post by prshah on 2008-05-09
> **piperdown10 said:**
> This is the ifconfig for the machine that I'm on:


For this "other" machine, can you post the output of ```
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by kevinatkins on 2008-05-09
Right OK.. so your cable modem is correctly setting the IP address on your other machine. Hmm, strange. 

OK, on the problem machine, you suggest you've tried enabling DHCP etc.

Just a checklist -

In System -> Administration -> Network, have you enabled 'Roaming Mode'? Try that if not. If still not working, turn off Roaming Mode and try DHCP.

Also, make sure the Host name is empty under the 'General' tab.

That's all I can think of really - it initially looked like a straightforward DHCP problem!

---

### Post by piperdown10 on 2008-05-09
I tried taking the roaming mode off and enabling a DHCP connection and still didn't get anything.

The output of cat /etc/network/interfaces is:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

and the output of cat /etc/resolv.conf is:

#generated by NetworkManager, do not edit!

search hsd1.tn.comcast.net.


nameserver 68.87.68.162
nameserver 68.87.74.162


In case you are wondering. I am using my laptop to get on to the internet but I want to use my desktop.

---

### Post by piperdown10 on 2008-05-10
I tried going in and removing the hostname from the General tab and everytime I check, it's back in there. I was reading somewhere about a PPPoE connection, or something like that. Would I need to do that?

---

### Post by piperdown10 on 2008-05-10
Also, I've been following [this]("http://ubuntuforums.org/showthread.php?t=786498") thread to see if it would be of any help and I'm still getting nothing. Does anyone have any ideas?

Thanks.

---

### Post by piperdown10 on 2008-05-12
*bump*

---

### Post by talon 2 on 2008-05-13
Just to be clear I am a novice with linux. I am running hardy heron and was having trouble not getting my internet connection. I enabled my wired roaming connection and it found it right away. Reading some of the posts it seems that you may have tried this. I did not change anything else accept install hardy heron and then run my updates and install them. Don't know if this helps at all?

---

### Post by piperdown10 on 2008-05-13
I am a novice as well.

I did try reinstalling Hardy and still nothing. What network card are you using? You said you had to update. Did you have to install any special drivers?

---

### Post by piperdown10 on 2008-05-15
Help....please....anyone?

---

