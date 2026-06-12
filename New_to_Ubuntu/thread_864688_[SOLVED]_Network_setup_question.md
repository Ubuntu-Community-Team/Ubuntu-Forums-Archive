---
title: "[SOLVED] Network setup question"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Arkeides on 2008-07-19
Hello World!,

I'd like to use my ubuntu machine as a hardware firewall. Here's my equipment:

1 x cable modem
1 x ubuntu box with 2 x NIC
1 x WRT54G Linksys Wireless Router
3 x Windows workstations behind the Wireless Router

Right now, the setup is cable modem -> wireless router -> workstations (windows & linux). I want to inject the linux box between the cable modem and the wireless router, but so far I've achieved little more than hours of down time and despair. Can anyone tell me how to do this, or point me towards an appropriate resource?

Thanks much,

Arkeides

---

### Post by neurostu on 2008-07-19
The best way to do this is to install Firestarter, its a gui front end to the firewall that is already installed in ubuntu.

Plug the modem into NIC 1 on the ubuntu machine. Plug the wireless router into NIC 2 on the Ubuntu machine.


You need to enable internet connection sharing across the two adapters, which you can do using firestarter.

---

### Post by freebeer on 2008-07-20
Your router should already be a pretty good firewall.

---

### Post by JagDragon on 2008-07-20
The Linksys WRT54G is already a superb hardware firewall, there is no need to use a computer as a firewall. All a hardware firewall does is looks for packets coming in, and if there was no request for them from a computer on the network, denies them access. The WRT54G already does that, and that is all a harware firewall can do.

To access the port forwarding menu, go to [http://192.168.1.1/Forward.asp](http://192.168.1.1/Forward.asp)

---

### Post by hyper_ch on 2008-07-20
well, depending on your model of the wrt54g I'd even suggest to replace the firmware with tomato which improves the quality quite a bit.

And firestarter is the old configuration tool in ubuntu... UFW is the new one.

---

### Post by Dedoimedo on 2008-07-20
Hello,

It's not a simple setup you are trying.

1. You will have to enable port forwarding on the Ubuntu machine.
2. You will have to enable SNAT both on the router and the Ubuntu machine and forwarding on the Ubuntu machine.

That's a bit of an overkill, as your router already does basic NAT and forwarding, and with just a few clicks, you can also forward ports.

I can help you set this up, but it's going to be LONG. And completely redundant.

Dedoimedo

---

### Post by The Cog on 2008-07-20
Before even thinking about what firewalling software to use, you need to enable IP packet forwarding. The command for this is:
**sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'**

You can check if forwarding is enabled with the command:
**cat /proc/sys/net/ipv4/ip_forward**
1 means forwarding is on.

To enable forwarding on boot, add this line to **/etc/sysctl.conf** :
net.ipv4.ip_forward=1

P.S.
It also occurs to me that you will need to do the following:
* Enable address translation (masquerading) on the internet-facing interface.
* Configure a DHCP server on the Linux box to tell the windows boxes what IP addresses they have, and what default gateway and DNS servers to use.

This is a nice reference site:
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)

---

### Post by Arkeides on 2008-07-20
Wow, the responses were quick, and I sense a common theme of "Yay Linksys". I'm no 'old hand' at Linux, so I think the best option for me--and for the people depending on my network's internet access--is to keep the WRT54G as my firewall. I think I gave in too easily to some technobabble from a friend, and didn't do enough research.

Thank you to everyone who responded. I can tell that it'd be a hugely complex operation and ultimately not worth the trouble, so I'll keep the current setup.

-Arkeides

---

