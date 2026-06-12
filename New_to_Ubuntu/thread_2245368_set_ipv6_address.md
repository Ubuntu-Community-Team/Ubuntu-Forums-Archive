---
title: "set ipv6 address"
date: 2014-09-23
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-09-23
Hi all,   how do I set ipv6 address if my ISP doesn't give me it automatically?  Is it possible at all?  Thanks ahead.

---

### Post by TheFu on 2014-09-23
You cannot just grab any ipv6 address and use it. It must be provided by the network admins. Also, all the equipment must work with ipv6 - most home routers don't, at least that hasn't been my experience.  Any DOCSIS3 or later cable modem does support IPv6, but earlier ones do not.

I would edit the /etc/network/interface file with the static IP data and subnet mask.  But I don't use CLI apps so much. Which exact desktop are you running? Perhaps someone else can help with point-n-click instructions ... or perhaps the ubuntuguide.org or [https://help.ubuntu.com/14.04/](https://help.ubuntu.com/14.04/) has some?

Of course, it might be possible to tunnel IPv6 through IPv4 from an external provider like he.com. I've never done that and would be worried about security - I'm always worried about security - since that would bypass the main edge router here. ;)

---

### Post by marchello_lippi2 on 2014-09-23
> all the equipment must work with ipv6 - most home routers don't, at least that hasn't been my experience.

how do I check that my router supports ipv6 ? 


> Which exact desktop are you running?

I'm using Lubuntu, but honestly I would like to set it via console if possible. 


> it might be possible to tunnel IPv6 through IPv4 from an external provider like he.com

Does it require the presence of external IP address at my router? I'm asking because my ISP started to provide only 10.XXX.YYY.ZZZ IP addresses to my router, that is why I'm interested in ipv6... I'd like to use my home pc from external places, it was possible just few days ago when my ISP provided 91.XXX.YYY.ZZZ IP addresses to my router... 

Any help?

---

### Post by TheFu on 2014-09-23
Lubuntu is important.  Edit the file mentioned above ... once you are provided an IPv6 address from a company who can do the routing.  Perhaps a refresher on internet routing is needed?  Episode 25 of "Security Now" podcast begins that.

I think you are screwed.  A reverse ssh-tunnel might be possible, but you'll need a host on the internet for that. A $2/month VPS should be enough.

I'd find another ISP.

[https://ipv6.he.net/certification/](https://ipv6.he.net/certification/) to learn more about ipv6.

---

### Post by grahammechanical on 2014-09-23
Network Manager icon>Edit Connections>Select connection>Select Edit>Select IPv6 Settings tab. It is set to Automatic by default. There is a drop-down menu of options.

Regards

---

### Post by marchello_lippi2 on 2014-09-23
> I think you are screwed. 
> A reverse ssh-tunnel might be possible, but you'll need a host on the internet for that. 
> A $2/month VPS should be enough.

Well, I do not want to use ssh, just access web interfase of my transmission. Hope it is possible for free. 


> I'd find another ISP.

Well, that is also possible. But my ISP now gives external IP address for only +2$/monthly. So it is a kind of sport to find free solution. But when it fails I will just pay 2 bucks more.

---

### Post by TheFu on 2014-09-23
> **marchello_lippi2 said:**
> Hope it is possible for free. 

Lots of things are ... some are not legal.  You could find a group of people on your ISP and share the $2/month VPS, but make certain the bandwidth allowed is only used for reverse control connections, not video streaming.  Or that VPS will need to be $20/month really quick.

> **marchello_lippi2 said:**
> 
> I'd find another ISP.

Well, that is also possible. But my ISP now gives external IP address for only +2$/monthly. So it is a kind of sport to find free solution. But when it fails I will just pay 2 bucks more.

I can see where 95% of the clients will be better off with 10.x.x.x addresses. It is just that small group who wants to run a server who need a public IP. There has to be a reverse-tunnel trick (like napster did) to get the connections working.  If both sides are behind NAT, then some 3rd party negotiation server is needed.  I vaguely remember a perl tool that did this - but it still needs to run on a machine on the internet with a real IP.  I'll google for a few min to see if ...

---

