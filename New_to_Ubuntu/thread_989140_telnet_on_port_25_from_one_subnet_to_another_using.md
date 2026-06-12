---
title: "telnet on port 25 from one subnet to another using Ubuntu as a router"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Halouji on 2008-11-21
Hello,

I need to telnet a smtp server from an Ubuntu box through another Ubuntu box.

Let's call the SMTP Server "smtpsrv", the first Ubuntu Box "ubuntu" and the second one "ubunter" because I want it to act as a router for my telnet request from "ubuntu" to "smtpsrv".

Both "Ubuntu" and "Ubunter" are running Ubuntu Server 8.0.4 LTS and have the following utilities installed: nano, traceroute, telnet. No GUI, only command-line available.

Here is the network config:
- "smtpsrv" has one NIC
- "ubuntu" idem
- "ubunter" has 2 NICs
- all the NICs are connected to the same Ethernet switch.

"smtpsrv" is in the 192.168.0.0/24 subnet and is ready to answer Telnet inquiries on 192.168.0.1 on standard SMTP port 25/tcp.

"ubuntu" has a working eth0 interface defined this way: 192.168.1.1/24 (static IP).

"ubunter" has:
- a working eth0 interface defined this way: 192.168.1.2/24 (static IP)
- a working eth1 interface defined this way: 192.168.0.2/24 (static IP)
- so "ubunter" can ping "ubuntu" on 192.168.1.1 and also ping "smtpsrv" on 192.168.0.1
- of course "ubunter" can telnet "smtpsrv" on 192.168.0.1:25

What's the easiest way to setup "ubuntu" and "ubunter" to allow "ubuntu" to telnet "smtpsrv" using "ubunter" as a router?

On the "ubuntu" point of view, I think my config is okay: I've added a route in the routing table to make "ubunter" the default gateway: route add default gw 192.168.1.2 and I checked with route -n if the result was okay.

But now as a Linux total newbee, I'm confused with what I have to do on "ubunter". I think I have to type a "route add" command, but what's the exact syntax?

When done, I think I would be able to ping and telnet "smtpsrv" without any problem.

Please help, I have a very blocking problem behind it all - many thanks for your help!

---

### Post by superprash2003 on 2008-11-21
i guess this command should help iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE where ethx is the interface connected to smtpserv

---

### Post by Halouji on 2008-11-21
Hello superprash2003,

Many thanks for your answer, but i need not to enable NAT and masquerading. "smtpsrv" i.e. the destination machine MUST see the originating IP address not the one of "ubunter".

According to your experience, isn't it possible to use the "route add" command to create a route on "ubunter" to allow communication between the 2 subnets?

The behaviour is: "ubunter" receives for example an ICMP request for "smtpsrv" coming from "ubuntu" so it just "passes" this ICMP request from eth0 to eth1 so "smtpsrv" receives it.

Please answer if I'm not clear enough.

---

### Post by superprash2003 on 2008-11-22
ok.. then you could use the route add command.. the syntax depends on your interface and the ip .. this should help [http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html)

---

### Post by Halouji on 2008-12-05
Hello superprash2003,

Thanks a lot for your messages. It's okay with activation of ip forwarding.

Regards

---

### Post by iskandarjon on 2008-12-06
Hello everybody!

A have a problem about telnet

when I am typing 

# telnet xxx.xxx.xxx.xxx 6000

It's running O.K.

But when I am typing by creating file and

[COLOR="Red"]-----------------------------------------------------
#!/bin/bash

telnet xxx.xxx.xxx.xxx 6000 <<EOF

LGI: OP="UserName", PWD="Password";

EOF
-----------------------------------------------------[/COLOR]

It's not running

Please anybody help me!

---

