---
title: "[SOLVED] Configuring openvpn to connect to a server"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by drtre on 2008-10-29
Hi,

Back in windows I used to create a VPN connection and connect to the server of which I had its IP and user/pass. But here I don't know how to setup a VPN connection to the server. I've also downloaded OpenVPN which I've been told is useful, but just don't know how to configure it. I'd appreciate any help.

---

### Post by The Cog on 2008-10-29
OpenVPN is a good stable VPN that plays well with NAT and firewalls. But you need OpenVPN on both client and server of course. Do you have control of both ends of the connection? If the server is someone else's, then you will have to use whatever tpe of VPN they have installed on the server. Are both ends Ubuntu?

For Ubuntu, you start by installng the OpenVPN package. Then I think you have to create the certificates, then make up the configuration files for both client and server.  I can probably provide good examples of the configuration files, but you will have to follow the instructions on the OpenVPN web site howto for making the certificates. [http://openvpn.net/howto.html](http://openvpn.net/howto.html)
 The server config file should go in /etc/openvpn/ so that it gets started on reboot. The client one should go somewhere else, and be launched when needed with a command like:
**sudo openvpn --config pathname/client.conf**

---

### Post by drtre on 2008-10-29
Thanks for the reply. I have no idea what the other end is. Maybe its a windows OS. I'm using this VPN for anonymous surfing and As far as I'm concerned I was doing it just with specifying the IP address of the server and providing the username/password. But here I really don't know about the other end and the configuration. So explain to me like you're explaining to a perfect n00b.:(

---

### Post by The Cog on 2008-10-30
In that case, I guess it is a Microsoft VPN. They use a protocol called PPTP. It is supported in Linux. I used ot once, and had to configure four or five text files by hand. I believe there is a GUI to do that now.
[http://www.google.com/search?hl=en&q=ubuntu+configure+pptp+vpn](http://www.google.com/search?hl=en&q=ubuntu+configure+pptp+vpn)

---

### Post by drtre on 2008-11-10
Thank u very much. I've found some articles about it. I'll try to make it work. If I face any problem I'll post it here.

---

