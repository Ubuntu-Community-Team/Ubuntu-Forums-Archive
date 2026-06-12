---
title: "Remote access question?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by rhcm123 on 2008-11-21
I would like to be able to remote access my server when i go on vacation later this year. However, I am only assigned 1 IP from verizon, as I only run a small home file server. (I don't want to pay the extra $40 a month for another IP.) I am confident my ip of aaa.bb.cc.ddd will not change (it hasn't since i got it, but I was just wondering, is there any way to change my modem settings so that i can ssh to my server over the net?)

I guess my real question is, can I have my modem redirect traffic from it's wan address to my server?

---

### Post by nhasian on 2008-11-21
are you connected directly to your dsl/cable modem or is there a router in between?  if you have a router, it may be compatible with one or more of the dynamic dns services like  [http://www.dyndns.com/](http://www.dyndns.com/)

with this free service even when your dyanamic ip address changes, your domain name will stay the same.

---

### Post by jonobr on 2008-11-21
heres a v useful link from a frequent poster on the forums
[http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

This takes into account the fact that your IP address can change and how you can remote desktop to connect to your machine from external networks.

---

### Post by rhcm123 on 2008-11-21
> **jonobr said:**
> heres a v useful link from a frequent poster on the forums
[http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

This takes into account the fact that your IP address can change and how you can remote desktop to connect to your machine from external networks.

That won't work, as my server is too old for a gui, and is only command line based. Sorry.

---

### Post by rhcm123 on 2008-11-21
> **nhasian said:**
> are you connected directly to your dsl/cable modem or is there a router in between?  if you have a router, it may be compatible with one or more of the dynamic dns services like  [http://www.dyndns.com/](http://www.dyndns.com/)

with this free service even when your dyanamic ip address changes, your domain name will stay the same.

My system is setup:
Interwho-modem-router-router-firewall-switch-server(s)

---

