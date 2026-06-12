---
title: "ipsec verify Two or more interfaces found failed"
date: 2016-09-21
forum: New to Ubuntu
---

### Post by mrblack720 on 2016-09-21
hi
i have problem with ipsec.

sudo ipsec verify

Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.38/K3.13.0-48-generic (netkey)
Checking for IPsec support in kernel                            [OK]
 SAref kernel support                                           [N/A]
 NETKEY:  Testing XFRM related proc values                      [OK]
    [OK]
    [OK]
Checking that pluto is running                                  [OK]
 Pluto listening for IKE on udp 500                             [OK]
 Pluto listening for NAT-T on udp 4500                          [OK]
Two or more interfaces found, checking IP forwarding           [COLOR=#ff0000] [FAILED][/COLOR]
Checking NAT and MASQUERADEing                                  [OK]
Checking for 'ip' command                                       [OK]
Checking /bin/sh is not /bin/dash                              [COLOR=#ffd700] [WARNING][/COLOR]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [COLOR=#ffd700][DISABLED][/COLOR]

---

### Post by SeijiSensei on 2016-09-21
Edit /etc/sysctl.conf and remove the hash mark at the beginning of the line
```
#net.ipv4.ip_forward=1
```
Then reboot.

---

