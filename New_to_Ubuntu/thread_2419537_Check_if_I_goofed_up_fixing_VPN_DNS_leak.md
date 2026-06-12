---
title: "Check if I goofed up fixing VPN DNS leak"
date: 2019-05-23
forum: New to Ubuntu
---

### Post by crip720 on 2019-05-23
Ran this command, want be sure if it worked the it should.  ```
sudo openvpn --dev tun                proto udp
                remote ca.windscribe.com 443
                
Thu May 23 15:45:27 2019 OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jun 22 2017
Thu May 23 15:45:27 2019 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Thu May 23 15:45:27 2019 ******* WARNING *******: all encryption and authentication features disabled -- all data will be tunnelled as cleartext
Thu May 23 15:45:27 2019 TUN/TAP device tun1 opened
Thu May 23 15:45:27 2019 UDPv4 link local (bound): [undef]
Thu May 23 15:45:27 2019 UDPv4 link remote: [undef]

```
Ran the three lines of code before  ```
[COLOR=#0000FF][FONT=&quot]script-security 2[/FONT][/COLOR]
[COLOR=#0000FF][FONT=&quot]up /etc/openvpn/update-resolv-conf[/FONT][/COLOR]
[COLOR=#0000FF][FONT=&quot]down /etc/openvpn/update-resolv-conf
```[/FONT][/COLOR]

---

### Post by TheFu on 2019-05-23
Does the routing table get modified?
Using UDP on port 443 seems odd. 443/tcp would be expected, but you'd need to have the VPN provider's list of protocols, ports, and encryptions used to connect correctly.

On the client-side, the VPN .ovpn file usually has about 20 settings which define how to connect to each specific service.  Perhaps windscribe has a posting about their settings?   My commercial VPN provider has specific files for every service type, each exit node, the type of encryption used and each port.  All those need to line up perfectly between the client and server to have an encrypted connection.

[https://windscribe.com/getconfig/openvpn](https://windscribe.com/getconfig/openvpn) seems to make the .ovpn files, but requires a login.

---

### Post by crip720 on 2019-05-23
This is what is in my config files without the keys.  ```
nobindauth-user-pass


resolv-retry infinite


auth SHA512
cipher AES-256-CBC
comp-lzo
verb 2
mute-replay-warnings
remote-cert-tls server
persist-key
persist-tun


key-direction 1
```

---

### Post by crip720 on 2019-05-23
Just did a tcp option and it kills up load(16mb to 0.51mb) on similar vpn server, download takes less of hit. Windscribe has about 10 different ports and UDP/TCP and AES-CBC or GCM.  Maybe you suggest better.  How would I check  routing table, remember I am a 'copy/paste' guy.

---

### Post by TheFu on 2019-05-23
$ route -n

My vpn config files don't have certs inside them. They point to external files.  I start the VPN using a command like this:
```
$ sudo openvpn CA_Toronto.ovpn
```
 
The client-side config file must have a line that says "client"

---

### Post by crip720 on 2019-05-23
Client is first on config file.  Done route first for vpn then without ```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface0.0.0.0         10.116.134.1    0.0.0.0         UG    50     0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp1s0f1
10.116.134.0    0.0.0.0         255.255.254.0   U     50     0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0f1
173.199.65.211  192.168.1.1     255.255.255.255 UGH   100    0        0 enp1s0f1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0f1
crip@cAspire ~> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp1s0f1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0f1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0f1
```  Not sure what the 169.x.x.x destination is, not my IP or my DNS.  The vpn server it was done on, has stopped connecting to internet, not sure if on their end, or something I did.  Looks like my bad, changed it back to automatic and working now.

---

