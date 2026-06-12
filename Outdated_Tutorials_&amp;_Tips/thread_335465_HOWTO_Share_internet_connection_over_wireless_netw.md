---
title: "HOWTO: Share internet connection over wireless network with DHCP"
date: 2007-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by sciyoshi on 2007-01-10
This HOWTO is based on [this forum post]("http://ubuntuforums.org/showthread.php?t=91370"), but also explains how to set up internet connection sharing with wireless and DHCP.

Say you want to use your desktop as a router, so that the topology looks something like this:

internet -> [eth0 - desktop - wlan0] -> laptop

with the laptop being assigned a dynamic IP address. To do this (replace eth0 and wlan0 appropriately for your setup - eth0 is the connection to the internet, and wlan0 is the wireless for your LAN):

[LIST=1]
[*] First, install the packages **dnsmasq**, **ipmasq**, and **dhcp3-server**, either with Synaptic or with the following command line:
```
sudo apt-get install dnsmasq ipmasq dhcp3-server
```
This may warn you that dhcp3-server could not be started - as we haven't edited the configuration yet, this is normal :-).

[*] Assign a static IP address for the wireless card on the desktop machine by editing the file **/etc/network/interfaces**. Add these lines to the end of the file (if you already see wlan0 somewhere else, delete that first):
```

auto wlan0
iface wlan0 inet static
     address 192.168.0.1
     netmask 255.255.255.0
     broadcast 192.168.0.255
     wireless-mode ad-hoc
     wireless-essid YOUR-NETWORK-SSID-HERE

```
You can also add encryption to this - see "man interfaces" for more details.

[*] Edit the file **/etc/default/dhcp3-server** by finding the line with **INTERFACES=""** and replacing it with
```

INTERFACES="wlan0"

```
This tells the DHCP server to listen on the local network for connections.

[*] Open the file **/etc/dhcp3/dhcpd.conf**. Find the following lines:
```

option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

```
and replace them with:
```

#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

```
by adding a pound sign to the beginning of the lines. Then paste this at the end of the file:
```

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
  option domain-name-servers 192.168.0.1;
#  option domain-name "internal.example.org";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}

```

[*] Set up IP masquerading and forwarding:
```

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
sudo dpkg-reconfigure ipmasq

```
The default answers should be fine.

[*] Set up DNS masquerading:
```

sudo dpkg-reconfigure dnsmasq

```

[*] Start everything up!
```

sudo ifdown wlan0
sudo ifup wlan0
sudo /etc/init.d/dnsmasq restart
sudo /etc/init.d/dhcp3-server restart

```
[/LIST]

If everything went well, you should now be able to get internet from a laptop just by connecting to this network!

Note: If the settings aren't saved after a reboot, try this:
```

sudo sh -c "echo \"net.ipv4.ip_forward = 1\" >> /etc/sysctl.conf"

```

Hope you enjoyed, post any problems and questions here :)

---

### Post by Spack971 on 2007-01-12
Very useful your howto but I have a problem when I restart my computer I can't connect to Internet until I restart the ipmasq service ](*,)

---

### Post by SuperMike on 2007-01-14
If you can afford to have the PC that's sharing the Internet connection to be on a static IP instead of DHCP, and all other systems be on DHCP, then you could implement [**[COLOR="DarkOrange"]_tinyproxy_[/COLOR]**]("http://www.ubuntuforums.org/showpost.php?p=683303&postcount=1") on it and have all the other workstations proxy through it. The side-effect of the web proxy, besides web content/adware filtering, is that all the Internet connections are funneled out through the system hosting the proxy.

For me, tinyproxy seems to be the easier route. However, if for some reason you can only implement your sharing host PC as a DHCP client, not a static client, then yes, this technique as specified above as the start of this thread is one workable solution.

---

### Post by Baellion on 2007-01-20
Hmm I've got the problem it doesn't work for me :/
I've got Ubuntu on the PC connected via wired router to the internet and would like to share this connection with a laptop (with WinXP). Made step by step what is written in this howto though it doesn't work.
During step 6 i encountered message:
[B]Restarting DNS forwarder and DHCP server: dnsmasqstart-stop-daemon: warning: failed to kill 5495: No such process
[/B]
Maybe it's the problem but i don't know how to solve it.

I'm quite fresh in Linux systems so I would be glad for any help.

---

### Post by BeachBum on 2007-02-01
Thanks for the howto, I'm almost completely up and running!

I can see and connect to the ad-hoc network provided by my workstation from my laptop using iwconfig (not network manager for some reason), and when I run jnettop on the workstation wireless interface, and ping a WAN address, I can see the laptop's IP.  I've gotten to the point where I can ping some websites via IP, and I can ping some, but not all I tried, using their www names, also firefox does not load any pages.  I'm assuming this to be some sort of DNS issue.

My current setup is as follows:

Wired Router(192.168.0.1)  -> [ eth0 (192.168.0.102) - workstation - ra0 (192.168.1.1) ] -> laptop eth1 (192.168.1.1xx)

Here are some outputs:

# iwconfig
ra0       RT61 Wireless  ESSID:"*_____*"  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 0A:17:0B:AB:6D:C3   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=83/100  Signal level:-45 dBm  Noise level:-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# ifconfig
ra0       Link encap:Ethernet  HWaddr 00:0E:2E:5E:7B:9E  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe5e:7b9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5751 errors:437 dropped:437 overruns:0 carrier:0
          collisions:3135 txqueuelen:1000 
          RX bytes:12372684 (11.7 MiB)  TX bytes:3957 (3.8 KiB)
          Interrupt:50 

# dhcpd.conf 
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.200;
  option domain-name-servers 216.178.92.98;
#  option domain-name "internal.example.org";
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}
-> I've tried setting domain-name-servers to both the localhost address, 192.168.1.1, and my ISP's DNS hosts with no luck

# interfaces
auto ra0
iface ra0 inet static
address 192.168.1.1
netmask 255.255.255.0
#       wireless-mode           ad-hoc
#       wireless-essid          *___________*
#       wireless-channel        12
-> the wireless options are provided in a separate .dat file and loaded at boot

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ra0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0           192.168.0.1   0.0.0.0                 UG   0      0        0 eth0

/var/log/syslog, messages and daemon show no errors regarding the wifi driver, dhcpd, dnsmasq or ipmasq.

Any suggestions?

Thanks!

---

### Post by aslamrahman on 2008-01-25
how to encryption my wireless network?

" You can also add encryption to this - see "man interfaces" for more details."

 i did'not get it.

---

### Post by flehnerz on 2008-04-03
Ok well that didn't do anything. Now I am left with non functioning wireless. I can still connect to an access point, it seems to be issuing IPs but no connectivity. Hmm....maybe I'll just reload Ubuntu or upgrade to the 8.04 beta. Wireless sucks anyways!

---

### Post by dclough on 2008-04-13
If things are still not working for you, you may want to try [this tutorial]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html").  Also some might find it easier to use Webmin instead of  the terminal.

Combining this HOWTO and the above tutorial, I have 90% of internet connection sharing working.  I just need to figure out why some sites load and others take forever.

---

### Post by spikoley on 2009-01-03
Great HowTo.  It deserves a bump.

---

### Post by otakuj462 on 2009-06-17
> **spikoley said:**
> Great HowTo.  It deserves a bump.

No longer current. As of Intrepid, Network Manager 0.7 provides much of this functionality, and is much easier to set up. See here for details:

[http://ubuntu-tutorials.com/2009/06/13/how-to-share-your-internet-connection/](http://ubuntu-tutorials.com/2009/06/13/how-to-share-your-internet-connection/)

---

### Post by otakuj462 on 2009-06-18
> **otakuj462 said:**
> No longer current. As of Intrepid, Network Manager 0.7 provides much of this functionality, and is much easier to set up. See here for details:

[http://ubuntu-tutorials.com/2009/06/13/how-to-share-your-internet-connection/](http://ubuntu-tutorials.com/2009/06/13/how-to-share-your-internet-connection/)

Actually, I take back what I said before; NetworkManager 0.7's Internet Connection Sharing feature is not a general replacement this kind of setup. It imposes several limitations which became apparent after I started to use it. These include: needing to have a user logged in in order to have the network auto-configure, and, for some reason, the created network disappears after a certain amount of time if no other users are connected to it (it reverts back to managed mode, and connects to whatever network is available). Also, I could never ultimately get it to work properly, as it would not correctly route DNS. I filed a bug report for this here: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/389006](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/389006)

Using the above technologies and instructions, however, I was sharing my wireless internet connection over another wireless NIC within a half-hour. Great howto, it absolutely got the job done!

---

### Post by VladX on 2009-11-05
Big thx! This is the only useful manual which I found that really works.

---

### Post by asel_ on 2009-12-20
Hi, it is completly nice thing.

But I've question about security :

I have a desktop pc running hardy and I use it as my home file sharing and storing server through wired lan eth0 to serve my windows based pc's and laptops.After this topic I wondering if I let hardy desktop connecting to internet 24/7 (i.e all time) to serve my poor windows based computers, is it danger to connect my windows based computers to internet through this server to the hardy based desktop which is connected to Internet 24/7 ?

Please I need to know. :)

---

### Post by asel_ on 2009-12-20
I mean is it secure from outside connections (may be hackers ,viruses, ...etc) to become through the poor MS windows computers connected to my network ?

( I hope it clear now)

---

### Post by Meghnaad on 2010-05-03
Works Like Charm on my Jaunty !
Thanks man you saved me a lot of $

---

