---
title: "Using Wireless at School"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by kvanb796 on 2008-11-05
I am dual booting Vista and Ubuntu 8.10.  My wireless at home works for both Ubuntu and Vista.  At school, however, it only works for vista.

The network at school comes up on Vista as "unnamed network," and automatically connects you after recognizing your IP address (which they have to add to their system in order for you to connect to the network.)  In Vista it takes 2-3 minutes for them to recognize your IP address and connect you.

I believe that you should have the same IP address as long as you are connecting from the same computer, correct?  Any ideas how could I make Ubuntu see and connect to this network?

---

### Post by Zzl1xndd on 2008-11-05
If its IP address then you would have to manually set it on the Ubuntu partition. IP's are not machine specific. Did the school assign you an IP address?

What might also be happening is filtering based on MAC (media access control) address.

---

### Post by kvanb796 on 2008-11-05
Hmm, now that you mention it, it could be the mac address but I thought it was the ip.  How do I set the ip address for the Ubuntu partition?

---

### Post by Zzl1xndd on 2008-11-05
Click on network manager > Select Manual configuration > Unlock network Settings > Select your wireless adapter > Click properties > Take the check out of roaming mode > and Under configuration there will be a static option.

---

### Post by DGortze380 on 2008-11-05
> **kvanb796 said:**
> Hmm, now that you mention it, it could be the mac address but I thought it was the ip.  How do I set the ip address for the Ubuntu partition?

If you automatically connect in windows (have never set a static address), then they are not identifying you by your IP, they're using DHCP.

If they're identifying you by your MAC (Common Practice), your MAC should not change between OS's, it's specific to your hardware.

post the output of the following commands
in windows:
ipconfig /all

in ubuntu:
ifconfig -a

---

### Post by kvanb796 on 2008-11-06
This is what I got for Ubuntu:
> eth0      Link encap:Ethernet  HWaddr 00:1e:68:9d:2f:11 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

pan0      Link encap:Ethernet  HWaddr 2e:cf:fe:a9:66:8e 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:2b:5c:4c 
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fe2b:5c4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2378939 (2.3 MB)  TX bytes:468254 (468.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-2B-5C-4C-00-00-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


This is what I got for Windows:
> Windows IP Configuration

   Host Name . . . . . . . . . . . . : Owner-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Atheros AR5008X Wireless Network Adapter
   Physical Address. . . . . . . . . : 00-21-63-2B-5C-4C
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::6cde:304e:5a8a:f4bc%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.4(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, November 06, 2008 8:18:20 AM
   Lease Expires . . . . . . . . . . : Friday, November 07, 2008 8:11:31 AM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : int.kaplan.com
   Description . . . . . . . . . . . : Marvell Yukon 88E8040T PCI-E Fast Etherne
t Controller
   Physical Address. . . . . . . . . : 00-1E-68-9D-2F-11
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{358190CC-18EB-4E74-A2EF-69BC0513F
B1D}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 7:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 11:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{3F35CBD9-CC49-4E3D-880C-6200EFA5F
342}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

---

### Post by handydan918 on 2008-11-06
You may have better luck connecting to multiple wireless AP's using wicd. Not sure if it's in the repos, but it works well for this kind of thing.

And +1 on the MAC filtering. That is common. Has the school given you a wep/wpa key?

---

### Post by DGortze380 on 2008-11-06
Your MAC and IP Address are the same in both Operating Systems. The MAC should not be causing the problem. It appears that your school is using DHCP, so it would all but impossible for them to control access via IP Address.

Did you have to run any software before using the school network?

---

### Post by jpoRS on 2008-11-06
Do you have to register your computer with the school in order to get wireless?  I know at my university we have to go to schoolname.edu/network and register our computer with the University before we could access wireless.  

And when I dual booted, both my XP partition and my Ubuntu partition had to be registered individually.

Good luck,
jim

---

### Post by kvanb796 on 2008-11-06
I have no idea what they did, they just took my laptop and did something.  Lol.  I spoke to my friend who worked for them, and he said they did it via recognizing your ip address.  I'm going to bring it to them and see what they can do though :(

> Click on network manager > Select Manual configuration > Unlock network Settings > Select your wireless adapter > Click properties > Take the check out of roaming mode > and Under configuration there will be a static option.

I'm sorry, I did not see network manager anywhere...

---

### Post by jpoRS on 2008-11-06
That sounds like it what I am talking about.  Hopefully they should be able to take care of it, but in my experience most student "tech support" folks are terrified of Linux.

Good luck,
jim

---

