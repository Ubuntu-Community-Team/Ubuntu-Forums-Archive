---
title: "Where oh where is iptables in Ubunt?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Tech4rce on 2008-09-04
Please help.  I'm trying to find where Ubuntu 7.10 Server keeps the iptables - so I can modify it.

I've created my own iptables rules - saved it in /etc/iptables. 
Made sure that it starts on boot.

Here is the deal.  I've STOPPED my iptables, went to [www.grc.com](www.grc.com) tested the firewall/ports.  Results came back saying that my server is in "Stealth" mode - What the F***??

So I figure that Ubuntu must have an iptables of it's own (or something) that blocks all ports.

The reason that I've "Stopped" my firewall is that I'm having problems connecting to it by VPN. Figured that I might as well kill the firewall to see happens.

Any help here would be great.
Thanks.

---

### Post by iaculallad on 2008-09-04
--Disregard--

---

### Post by hyper_ch on 2008-09-04
use nmap from another computer and not grc

---

### Post by ukripper on 2008-09-04
This may help [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by jerome1232 on 2008-09-04
> **hyper_ch said:**
> use nmap from another computer and not grc

+1 

That site was never reported accurate results for me.

---

### Post by Tech4rce on 2008-09-06
I got them to work.  Not to worry, but thanks to all who replied.

---

