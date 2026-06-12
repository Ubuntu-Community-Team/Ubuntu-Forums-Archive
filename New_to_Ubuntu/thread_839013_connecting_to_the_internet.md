---
title: "connecting to the internet"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-24
Hiya,,

got a quick question....i've installed ubuntu server edition on a PC which i could connect to the university n/w via ethernet cable.now how do i configure it so that i could access the internet(ofcourse via the uni LAN)....
do i have to get the uni/isp nameservers domain names etc etc...?

---

### Post by p_quarles on 2008-06-24
Assuming that you have permission to connect this computer to the network, the router should take care of providing the IP address, either by special assignment or by DHCP. 

If you are asking how to make this server available over the public internet, that's more a question for your university's IT department. First, you'll need their permission. Second, you'll need them to set up network address translation or DNS -- requests to your subdomain would be redirected by their routers to your computer. That's not something you can do without their assistance.

---

### Post by ub007 on 2008-06-24
'If you are asking how to make this server available over the public internet' -not really...

however,i wish to setup an intranet using this server,so would rather set my own static ip for it,and also install dhcp n configure it to lease out ips to the intranet.but when i do that,will i be messing up with the uni network?to be more precise,a)the dhcp installed on my server may interfere with the uni n/w comps 
b)you mentioned 'the router should take care of providing the IP address, either by special assignment or by DHCP. 'once i change the settings and issue the static ip,would i end up losing connectivity...?
-the idea is the server should dish out ips using dhcp to the local intranet,at the same time be able to conect to the uni n/w without creating any conflicts...any work arounds?i posted a similar thread inthe n/w & wireless section,but not much help...

cheers

---

### Post by p_quarles on 2008-06-24
> **ub007 said:**
> i wish to setup an intranet using this server,so would rather set my own static ip for it,and also install dhcp n configure it to lease out ips to the intranet.but when i do that,will i be messing up with the uni network?
They would have to permit the static IP before you could obtain that (i.e., it depends on how their router is configured). Setting up a separate internal network won't cause any trouble for the university's network, no. 

> to be more precise,a)the dhcp installed on my server may interfere with the uni n/w comps
I don't see how. DHCP servers are designed to run in layers, and can theoretically do so almost infinitely.  
> b)you mentioned 'the router should take care of providing the IP address, either by special assignment or by DHCP. 'once i change the settings and issue the static ip,would i end up losing connectivity...?
I'm not sure I understand the question. Your server would not be issuing its own IP address: it would obtain that from the next higher level IP address server. The server can only assign IP addresses to machines under its authority.

> -the idea is the server should dish out ips using dhcp to the local intranet,at the same time be able to conect to the uni n/w without creating any conflicts...any work arounds?i posted a similar thread inthe n/w & wireless section,but not much help...

cheers
I don't see any problems with this setup. Have you encountered any? If you haven't so far, I'd say this setup should be very easy.

---

### Post by cariboo on 2008-06-24
It seems to me that you've asked this same question in at least three different posts. Wouldn't it be better to ask this question in the proper forum. Try the network or server forums, you may get better help. An other thing I would suggest is to talk to someone in your IT Department as to what you can and can't do.

Jim

---

