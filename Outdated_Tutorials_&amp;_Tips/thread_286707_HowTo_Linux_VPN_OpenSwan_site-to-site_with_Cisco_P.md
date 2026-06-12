---
title: "HowTo Linux VPN OpenSwan site-to-site with Cisco PIX"
date: 2006-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-10-28
[i]
originally posted at:
[http://howtoforums.net/viewtopic.php?t=92](http://howtoforums.net/viewtopic.php?t=92)
[/i]

This HowTo is to help you setup a Site To Site VPN between Linux OpenSwan VPN and Cisco PIX FireWall...


Scenario:
```

Left Network [Linux OpenSwan]	Site-to-Site VPN	Right Network [Cisco PIX 515]
Public VPN IP: 70.18.18.28		<-->		Public VPN IP: 60.50.7.194
Internal Network: 192.168.1.0/24	<-->		Internal Network: 172.16.10.0/24
OpenSwan Internal IP: 192.168.1.251	<-->		Cisco IP: 60.50.7.194

			<--VPN Authentication via PreShared Keys-->

```


CISCO PIX 515 Configuration
Ver 7.05

```

access-list outside_cryptomap_120 extended permit ip 192.168.1.0 255.255.255.0 60.50.0.0 255.255.0.0 
access-list outside_cryptomap_120 extended permit ip 60.50.0.0 255.255.0.0 192.168.1.0 255.255.255.0 
access-list outside_cryptomap_120 extended permit ip 192.168.1.0 255.255.255.0 172.16.10.0 255.255.255.0 
access-list outside_cryptomap_120 extended permit ip 172.16.10.0 255.255.255.0 192.168.1.0 255.255.255.0 
access-list inside_outbound_nat0_acl extended permit ip 192.168.1.0 255.255.255.0 172.16.10.0 255.255.255.0 
access-list inside_outbound_nat0_acl extended permit ip 172.16.10.0 255.255.255.0 192.168.1.0 255.255.255.0 
access-list inside_outbound_nat0_acl extended permit ip 192.168.1.0 255.255.255.0 60.50.0.0 255.255.0.0 
access-list inside_outbound_nat0_acl extended permit ip 60.50.0.0 255.255.0.0 192.168.1.0 255.255.255.0

nat (inside) 0 access-list inside_outbound_nat0_acl
nat (dmzweb) 0 access-list inside_outbound_nat0_acl

no sysopt connection permit-ipsec

crypto ipsec transform-set ESP-3DES-MD5 esp-3des esp-md5-hmac 
crypto map outside_map 120 match address outside_cryptomap_120
crypto map outside_map 120 set peer 70.18.18.28 
crypto map outside_map 120 set transform-set ESP-3DES-MD5
crypto map outside_map interface outside

isakmp identity address 
isakmp enable outside
isakmp policy 20 authentication pre-share
isakmp policy 20 encryption 3des
isakmp policy 20 hash sha
isakmp policy 20 group 2
isakmp policy 20 lifetime 86400

tunnel-group DefaultRAGroup general-attributes
 authentication-server-group (outside) none
tunnel-group 70.18.18.28 type ipsec-l2l
tunnel-group 70.18.18.28 ipsec-attributes
 pre-shared-key *


```



Here’s on an older version 6.3(5) Configuration

```

access-list outside_cryptomap_120 permit ip 192.168.1.0 255.255.255.0 60.50.0.0 255.255.0.0 
access-list outside_cryptomap_120 permit ip 60.50.0.0 255.255.0.0 192.168.1.0 255.255.255.0 
access-list outside_cryptomap_120 permit ip 192.168.1.0 255.255.255.0 172.16.10.0 255.255.255.0 
access-list outside_cryptomap_120 permit ip 172.16.10.0 255.255.255.0 192.168.1.0 255.255.255.0 
access-list inside_outbound_nat0_acl permit ip 192.168.1.0 255.255.255.0 172.16.10.0 255.255.255.0 
access-list inside_outbound_nat0_acl permit ip 172.16.10.0 255.255.255.0 192.168.1.0 255.255.255.0 
access-list inside_outbound_nat0_acl permit ip 192.168.1.0 255.255.255.0 60.50.0.0 255.255.0.0 
access-list inside_outbound_nat0_acl permit ip 60.50.0.0 255.255.0.0 192.168.1.0 255.255.255.0

nat (inside) 0 access-list inside_outbound_nat0_acl
nat (dmzweb) 0 access-list inside_outbound_nat0_acl

crypto ipsec transform-set ESP-3DES-MD5 esp-3des esp-md5-hmac 
crypto map outside_map 120 ipsec-isakmp
crypto map outside_map 120 match address outside_cryptomap_120
crypto map outside_map 120 set peer 70.18.18.28
crypto map outside_map 120 set transform-set ESP-3DES-MD5
crypto map outside_map interface outside


isakmp enable outside
isakmp key ******** address 70.18.18.28 netmask 255.255.255.255 no-xauth no-config-mode 
isakmp identity address
isakmp policy 20 authentication pre-share
isakmp policy 20 encryption 3des
isakmp policy 20 hash sha
isakmp policy 20 group 2
isakmp policy 20 lifetime 86400
 

```



The Linux OpenSwan Box (Ubuntu 6.06 Dapper Server )

root@vpngw:~# cat /etc/ipsec.conf
```

# /etc/ipsec.conf - Openswan IPsec configuration file
# RCSID $Id: ipsec.conf.in,v 1.15.2.2 2005/11/14 20:10:27 paul Exp $
# This file:  /usr/share/doc/openswan/ipsec.conf-sample
#
# Manual:     ipsec.conf.5
version 2.0     # conforms to second version of ipsec.conf specification

#http://www.wlug.org.nz/FreeSwanToCiscoPix
#http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch35_:_Configuring_Linux_VPNs#Introduction


conn tunnelipsec
        type=           tunnel
        authby=         secret
        #RRT
        left=           192.168.1.251
        leftsubnet=     192.168.1.0/24
        leftnexthop=    %defaultroute
        #SAA
        right=          60.50.7.194
        rightsubnet=    172.16.10.0/24
        rightnexthop=   %defaultroute
        esp=            3des-md5
        keyexchange=    ike
        pfs=            no
        auto=           start

#Disable Opportunistic Encryption
include /etc/ipsec.d/examples/no_oe.conf

```


root@vpngw:~# uname -a
```

Linux vpngw 2.6.15-27-server #1 SMP Sat Sep 16 02:57:21 UTC 2006 i686 GNU/Linux

```

root@vpngw:~# route
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0   *               255.255.255.0   U     0      0        0 eth0
172.16.10.0     192.168.1.1   255.255.255.0   UG    0      0        0 eth0
default         192.168.1.1   0.0.0.0         UG    0      0        0 eth0

```


root@vpngw:~# cat /etc/ipsec.secrets
```

#For Pre-Shared Keys Use this Format:
#  vpn1-ip-address vpn2-ip-address : PSK "key in quotations"
192.168.1.251 60.50.7.194 : PSK "xxxxxxxxx"

```


Also this must be done....
root@vpngw:~# cat HowTo_NAT.txt
```

IP forwarding
Each Linux VPN device needs to have routing or IP forwarding enabled. To enable it, simply add an ip_forward entry to the /etc/sysctl.conf file.

#
# File: /etc/sysctl.conf
#
#---------------------------------------------------------------
# Enable routing (IP forwarding)
#---------------------------------------------------------------

net/ipv4/ip_forward = 1

```
 

Now use the sysctl -p command to activate the settings.

```

[root@vpngw tmp]# sysctl -p
...
...
net.ipv4.ip_forward = 1


```


[i]
for search engines
IPSec VPN between Linux and a Cisco PIX
Linux IPSec VPN Site2Site
Configuring Linux VPNs
Configuring an IPSec VPN between OpenSwan and a CiscoPix
Configuring an IPSec VPN between FreeSwan and a CiscoPix
HowTo OpenSwan
HowTo Linux Site to Site VPN
Linux Unix VPn
Cisco to Linux VPN
HowTo OpenSwan Ubuntu
HowTo OpenSwan Debian
[/i]

Big Thanks to my distant Cisco Guru freind, Shawn de Souza


Have Fun!!! :)

"Forgiving is not a Weakness, rather a Godly Strength"
--Jacob
[http://howtoforums.net](http://howtoforums.net)

---

### Post by amilauduwerella on 2008-11-14
Hi,


I was trying to create a vpn site-to-site tunnel between a Cisco ASA 5520 and a Linux box.

i think the PIX and ASA are same configuring.

but i cannot establish the connection.:(

My linux box do not assigned a Public IP Address it self, but it has a static NAT.

These are the configuration the guys sent me, who have this Cisco ASA, I am not sure how to put these info in ipsec.conf
____________________________________________________________
Phase1           Key Exchange: 3DES, Data integrity: SHA, DH Group2

Phase2           Encryption: 3DES, Data integrity: SHA, DH Group 2

                      Perfect Forward Secrecy.

_____________________________________________________________

Can somebody please help me to configure my ipsec.conf

and establish this connection.

---

