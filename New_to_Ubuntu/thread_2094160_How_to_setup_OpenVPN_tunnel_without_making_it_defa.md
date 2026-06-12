---
title: "How to setup OpenVPN tunnel without making it default"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by junkyhlm on 2012-12-13
I have another question thread running where i ask for help with tunneling traffic from one specific program ([**Help with rtorrent and openvpn (anonine)**]("http://ubuntuforums.org/showthread.php?t=2093609")) but in this thread i want help with setting up a OpenVPN tunnel correctly.

I'm trying to get my OpenVPN setup to work at home. I'm running a server with rtorrent and apache2 and when i'm setting up the tunnel it routes all the traffic through it.

**What i want:** Just to setup the tunnel without diverting any traffic through it. I just want it to run in preparation for when i've gotten help or found an answer to my troubles with routing traffic from one specific program, rtorrent in this case.

---

### Post by SeijiSensei on 2012-12-13
If the configuration is defined in a .conf file in /etc/openvpn, you can have it start on boot by running:

```
sudo update-rc.d openvpn defaults
```

If your computer is configured as a client (i.e., the .conf file includes a "remote" directive), then OpenVPN will start an attempt to connect to the server.  Once it connects it will just be available, but unless you have traffic destined for the other end of the tunnel, it will just be waiting.

---

### Post by junkyhlm on 2012-12-14
> **SeijiSensei said:**
> If the configuration is defined in a .conf file in /etc/openvpn, you can have it start on boot by running:

```
sudo update-rc.d openvpn defaults
```

If your computer is configured as a client (i.e., the .conf file includes a "remote" directive), then OpenVPN will start an attempt to connect to the server.  Once it connects it will just be available, but unless you have traffic destined for the other end of the tunnel, it will just be waiting.

Thank you for your answer. I just have one file in ./openvpn/ and its named "update-resolv-conf" and dont seem to be the file i'm looking for. 

When im setting up the tunnel i use preconfigured files from the VPN provider that looks like this:
```

client

dev tap

proto udp

remote openvpn.anonine.net 1194
remote openvpn.anonine.net 1195
remote openvpn-2.anonine.net 1196
remote openvpn-2.anonine.net 1197
remote openvpn-3.anonine.net 1198
remote openvpn-3.anonine.net 1199
remote openvpn-4.anonine.net 1200
remote openvpn-4.anonine.net 1201

remote-random

resolv-retry infinite

auth-user-pass

nobind

persist-key
persist-tun

ca anonine.ca.crt

```

---

### Post by junkyhlm on 2012-12-20
My problem is this:

I've managed to setup an working VPN tunnel but it channel ALL my outbound traffic through it. My apache webservers become "offline" since my domain does'nt find my sites. I want to setup a VPN tunnel without the apache-traffic beeing sent throught it.

Please help.

---

### Post by scoobyNZ on 2013-01-17
Hi,

I have the exact same problem / issue.

Did you manage to resolve this?

C

---

