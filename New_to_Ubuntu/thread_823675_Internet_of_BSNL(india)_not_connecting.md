---
title: "Internet of BSNL(india) not connecting"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by drsubhadip on 2008-06-09
i m very new to linux and also to ubuntu..
i live in kolkata ,india..
can not connect to BSNL  broadband through ubuntu..
the ifconfig say s the following...



subha@subha-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:19:d3:6e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fe19:d36e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:522 (522.0 B)  TX bytes:7663 (7.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51300 (50.0 KB)  TX bytes:51300 (50.0 KB)




now i ve dual boot with windows xp..
the ipconfiguration fo xp is as follows....

Windows IP Configuration



        Host Name . . . . . . . . . . . . : abc-e0a4fd8e35a

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No

        DNS Suffix Search List. . . . . . : local.lan



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : local.lan

        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection

        Physical Address. . . . . . . . . : 00-11-11-19-D3-6E

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 192.168.1.2

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.1

        DHCP Server . . . . . . . . . . . : 192.168.1.1

        DNS Servers . . . . . . . . . . . : 192.168.1.1

        Lease Obtained. . . . . . . . . . : Thursday, June 05, 2008 11:18:51 AM

        Lease Expires . . . . . . . . . . : Thursday, June 05, 2008 11:18:51 PM



PPP adapter Dataone:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface

        Physical Address. . . . . . . . . : 00-53-45-00-00-00

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 117.194.195.238

        Subnet Mask . . . . . . . . . . . : 255.255.255.255

        Default Gateway . . . . . . . . . : 117.194.195.238

        DNS Servers . . . . . . . . . . . : 218.248.255.162

                                            218.248.255.139

        NetBIOS over Tcpip. . . . . . . . : Disabled



that is what i can tellu every body..
can any body help me to connect to the broadband through ubuntu......
please..
help me..
thanks in advance..
 I LOVE UBUNTU.. it is great:):):)

---

### Post by ukripper on 2008-06-09
Are you using modem or router?

---

### Post by drsubhadip on 2008-06-09
using modem nokia siemens c2110

---

### Post by ukripper on 2008-06-09
> **drsubhadip said:**
> using modem nokia siemens c2110

use this guide - [http://www.ubuntu-in.org/wiki/Broadband_Howto](http://www.ubuntu-in.org/wiki/Broadband_Howto)

---

### Post by drsubhadip on 2008-06-09
problem solved with pppoeconf.........

---

### Post by ukripper on 2008-06-09
> **drsubhadip said:**
> problem solved with pppoeconf.........

great! mark this thread as SOLVED.

---

### Post by drsubhadip on 2008-06-10
> **ukripper said:**
> great! mark this thread as SOLVED.

HOW CAN DO THAT?
 that is how can i say to it as solved.....
please suggest..

---

### Post by drsubhadip on 2008-06-10
thanks everybody

---

