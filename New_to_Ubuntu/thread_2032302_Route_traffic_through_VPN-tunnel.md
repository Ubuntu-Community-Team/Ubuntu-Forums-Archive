---
title: "Route traffic through VPN-tunnel"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Bufeu on 2012-07-23
I have just bought a VPN connection from a trusted VPN provider. Installed OpenVPN using apt-get:
```
sudo apt-get install openvpn resolvconf && sudo apt-get install network-manager-openvpn
```I tried to connect using the Network Manager successfully, without any problems. Then, I noticed that Firefox said "Connection Timeout", no matter what page i visited. Pinging didn't work either. I thought it was a temporary problem and waited to see if it would work later.
Today, I tried again, but with the same result. I opened Wireshark and saw that NO PACKET AT ALL passed through the VPN-tunnel. I realized a had to route the traffic. I have never done that before and it would be nice if someone could tell me how I do that.
To make it easier for you to help me, I will post what *route -n* says:

Without VPN:
```
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
192.168.1.0 0.0.0.0 255.255.255.0 U 1 0 0 eth0
```With VPN (without routning):
```
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 10.8.0.221 0.0.0.0 UG 0 0 0 tun0
10.8.0.1 10.8.0.221 255.255.255.255 UGH 0 0 0 tun0
10.8.0.221 0.0.0.0 255.255.255.255 UH 0 0 0 tun0
46.21.99.25 192.168.1.1 255.255.255.255 UGH 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
192.168.1.0 0.0.0.0 255.255.255.0 U 1 0 0 eth0 
```I'm using a wired connection (eth0) and 168.192.1.1 is my gateway. 46.21.99.25 are the IP of the VPN server.
If it's possible, I want to use 95.211.10.3 as my DNS-server.

---

### Post by richpri on 2012-07-23
You now have two gateways: 
Your eth0 gateway should still be at 192.168.1.1
And it looks like your VPN server gateway is 46.21.99.25
I am also assuming that your local net is 192.168.1.0/24

First you have to decide which gateway will be the default gateway. 
Then you have to determine all of the IP address ranges [subnets]
that you want routed to the non default gateway.
 
Lets assume that the eth0 gateway will be your default and
that you want the 46.21.99.00/24 and the 46.20.00.00/24 
subnets to be routed to the VPN.

First you always should have a loopback route 

127.0.0.0 0.0.0.0 255.255.0.0 U 40 0 0 lo

Next you need a route for your local area network [LAN]

192.168.1.0 0.0.0.0 255.255.255.0 U 40 0 0 eth0

Next you need routes for your VPN subnet

46.21.99.00 46.21.99.25 255.255.255.0 UG 40 0 0 tun0
46.20.00.00 46.21.99.25 255.255.255.0 UG 40 0 0 tun0

Finally you need a default route [this has to be last!]

0.0.0.0 192.168.1.1 0.0.0.0 UG 40 0 0 eth0

---

### Post by Bufeu on 2012-07-24
Thanks. What happens if my VPN does down or if I disconnect? It's very annoying to route everytime I disconnect. Is it any script for this?

---

### Post by richpri on 2012-07-24
perhaps this discussion would be helpful

[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)

---

### Post by Bufeu on 2012-07-24
> **richpri said:**
> perhaps this discussion would be helpful

[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)
Doesn't work foe me.

---

