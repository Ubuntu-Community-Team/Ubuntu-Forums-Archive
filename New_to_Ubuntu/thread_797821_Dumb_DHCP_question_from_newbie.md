---
title: "Dumb DHCP question from newbie"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by phoenix1963 on 2008-05-17
I'm sure the answer is simple... just intalled kubuntu 8.04 and I can't manually set my IP address to 192.168.p.q/255.255.255.0 - I get an error message "invalid gateway IP address" when I try to set it to my router's address of 192.168.n.m using System-Stettings->Network-Stettings->Administrator...

I can only get network/internet access if I use DHCP from my router, which I normally have turned-off for various security reasons (also why I'm not telling the exact internal IPs!)

Appreciate some help,

phoenix1963

---

### Post by Monicker on 2008-05-17
Are you making sure the ip address is in the same subnet as the router?   And what gateway are you going to use if the router is turned off?

With a subnet mask of 255.255.255.0, both the gateway and workstation need to be in the range of 192.168.x.1 through 192.168.x.254

Gateway: 192.168.1.1
Computer: 192.168.1.50

You can't do

Gateway: 192.168.1.1
Computer: 192.168.2.50


Unless you use a wider subnet mask than 255.255.255.0, such as 255.255.0.0, for example.

---

### Post by phoenix1963 on 2008-05-17
> **Monicker said:**
> Are you making sure the ip address is the same subnet as the router?   And what gateway are you going to use if the router is turned off?

With a subnet mask of 255.255.255.0, both the gateway and workstation need to be in the range of 192.168.x.1 through 192.168.x.254

Gateway: 192.168.1.1
Computer: 192.168.1.50

You can't do

Gateway: 192.168.1.1
Computer: 192.168.2.50


Unless you use a wider subnet mask than 255.255.255.0, such as 255.255.0.0, for example.

Understood, they're both on the same subnet, I meant 255.255.0.0, duh.

With DHCP switched on on the router I'm OK with auto DHCP on the PC, with manual DHCP on the PC and still with DHCP supplied by the router I get network unreachable.

This isn't a proxy set-up issue is it (terribly ignorant here)? It's as if the PC can't route private IPs when manually set.

Thanks for the interest,

phoenix1963

---

### Post by phoenix1963 on 2008-05-17
For some completely mysterious reason, manual setting now works - and my nvidia & X settings have returned after vanishing after an Adept update. Just hope it's not just a temporary DHCP lack of expiry issue....

I was hoping kubuntu would be a bit less mysterious than Windoze!

phoenix1963

---

### Post by Monicker on 2008-05-17
It may just be how the router itself is hard coded.  I know someone at work who also had a router which would not pass any trafffic if the ip address was not assigned by the router itself.  I guess it could be thought of as a security measure, but his was the only one I've come across myself that behaved in such a manner.

---

### Post by Monicker on 2008-05-17
> **phoenix1963 said:**
> For some completely mysterious reason, manual setting now works - and my nvidia & X settings have returned after vanishing after an Adept update. Just hope it's not just a temporary DHCP lack of expiry issue....

I was hoping kubuntu would be a bit less mysterious than Windoze!

phoenix1963

Interesting.  I do not know why that would have happened with kubuntu, though I have not used it much myself.  My laptop which runs KDE in Debian has never done that.

---

### Post by phoenix1963 on 2008-05-17
It isn't the router, I've two Windows PCs with hardwired IPs on it too.

I'm using kubuntu so I can have a Windows independent machine running wireshark (to monitor my other two PCs because I'm paranoid) because my Windows PCs or router have been attacked too many times while merely browsing recently. It's become really hard to be sure there's nothing bad on them these days.

Anyway, thanks for the help Moniker.

---

