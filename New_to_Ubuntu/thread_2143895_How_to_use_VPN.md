---
title: "How to use VPN?"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by asteriks on 2013-05-10
Hi, you can move this topic to server platforms forum if you want.

I tried yesterday to install many different VPN clients and in the  end I understood I must have some login information in order to use VPN.

so, after I install OpenVPN, where to find Gateway (I suppose it is IP  address, should I write my local IP address or some server address?), CA  file, Certificate, key, username and password?

I believe I should connect client to some server, but I don't have idea  where to find OpenVPN server and its IP address and username and  password and certificates...

I tried one time even with my email hosting, they let me to download zip  file with VPN configuration files, but I didn't succeed to use OpenVPN  to connect to my email.
but I am interested to use some free VPN for Kubuntu for Internet generally, not only for email.

some tutorial on youtube doesn't say where he downloaded his openvpn configuration (zip) file...

should I register myself at some server in order to be able to use openvpn? if yes, which server? I don't have any idea...

-------------------------

today I tried PPTP and again no success, here is video of desktop screenshot, you can tell me where I make mistake, video shows that there are the same parameters from website and in my vpn network inreface: [http://s619.photobucket.com/user/globspace/media/linuxproblems/VPNproblem_zps5f5b9c71.mp4.html](http://s619.photobucket.com/user/globspace/media/linuxproblems/VPNproblem_zps5f5b9c71.mp4.html)

VPN Type:   **PPTP VPN **                                         
Encryption:   **Enabled (or Auto) **
VPN Server:   **superfreevpn.com**
 VPN Username:   **free**
 VPN Password:  1622

**I tried also: **

debian@debian:~$ iptables -A INPUT -i eth0 -p tcp --sport 1723 -m state --state ESTABLISHED -j ACCEPT

debian@debian:~$ sudo iptables --append INPUT --protocol 47 --jump ACCEPT

debian@debian:~$ sudo iptables --append INPUT --protocol tcp --match tcp --destination-port 1723 --jump ACCEPT

---

### Post by 2F4U on 2013-05-10
I guess you need to do a bit of reading. OpenVPN is a secure point-to-point connection based on a public key infrastructure, so its not done by simply installing a program.

[http://en.wikipedia.org/wiki/OpenVPN](http://en.wikipedia.org/wiki/OpenVPN)
[http://openvpn.net/index.php/open-source.html](http://openvpn.net/index.php/open-source.html)
[https://help.ubuntu.com/12.04/serverguide/openvpn.html](https://help.ubuntu.com/12.04/serverguide/openvpn.html)

---

### Post by asteriks on 2013-05-11
Hi, then why this didn't work:
VPN Server:   **superfreevpn.com**
 VPN Username:   **free**
 VPN Password:  1622

---

