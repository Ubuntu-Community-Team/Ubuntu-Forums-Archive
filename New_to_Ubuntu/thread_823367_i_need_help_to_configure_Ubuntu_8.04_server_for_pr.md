---
title: "i need help to configure Ubuntu 8.04 server for proxy"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by rr.villanueva on 2008-06-09
Hey Folks,

Could you please help me to configure the Ubuntu 8.04 Server, basically am poor of knowledge in Linux this is my first time to use the OS of Linux, am her right now in my company accommodation and one of my coworker subscribe a DSL with 512Kbps and Linksys DLS modem 4ports with a wireless, we have a (5) five desktop user at a time but 512Kbps speed is not enough to connect all, I buy one Acer Desktop with (2) two Network Card to use Linux Proxy Server with the Ubuntu 8.04 Server to share in internet in my follow co worker could you please help me to configure the Server her are the list of hardware and software that I have

Linksys Modem
ADSL port: connected to PPPoe internet connect (ISP provider  DHCP)
Port1: 192.168.1.1/24 (default internet gateway from the linksys)

Server
OS : Ubuntu 8.04 Server
HW: Aces Aspire M3630
NIC1: Broadcom Ethernet NIC 
IP address: 192.168.1.2/24
Gateway: 192.168.1.1

NIC2: 3Com Gigabit NIC
IP address: ???.???.???.???
Gatway: ???.???.???.???

Client 1 up to 5 Desktop Computer
OS : windows XP SP2
IP address1 ~ 5:    ???.???.???.???
Gatway: ???.???.???.???

SWITCH
3COM 8 Port 100Mbps / 1Gbps

I install already the Ubuntu 8.04 Server in my Acer Desktop to uses as a proxy server but the problem I don’t know any things in the command prompt how to manipulate and to configure the proxy server and DCHP to share the internet to my co worker and also I need to know if its possible to use the Linksys wireless device from the modem to use access point and share internet direct from the server? And also its is possible to install KDE Desktop in UBUNTU 8.04 server to use a Graphics desktop, please help me your reply are big help and opportunity to me to learn the OS of Linux.

[email]rr.villanueva@gmail.com[/email]

---

### Post by Cypher on 2008-06-09
You need to configure Squid to do what you want..perhaps these two links will direct you in the right direction..
[http://linux.about.com/od/ubusrv_doc/a/ubusg26t01.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg26t01.htm)
[http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/](http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/)

---

### Post by rr.villanueva on 2008-06-09
> **Cypher said:**
> You need to configure Squid to do what you want..perhaps these two links will direct you in the right direction..
[http://linux.about.com/od/ubusrv_doc/a/ubusg26t01.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg26t01.htm)
[http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/](http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/)
Thank You for the respond Cypher! I appreciate your help
Regards

[email]rr.villanueva@gmail.com[/email]

---

