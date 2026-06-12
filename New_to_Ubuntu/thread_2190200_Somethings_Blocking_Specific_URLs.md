---
title: "Somethings Blocking Specific URLs"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by Quarkrad on 2013-11-26
My wife (12.10) cannot access two specific urls via firefox - but I can (13.04) and we are both running ff ver 25.   So .... I renamed her .mozilla folder, removed ff via synaptic and reinstalled a fresh copy.  After putting her saved passwords and bookmarks back I confidently tried the urls but they still refused to load.  Her ff did not have a firewall so I now installed one as per my machine (gufw).  We are both on the same local lan with static ip addresses and hence access the internet via the same router - but I can access these sites and she cannot.  When I ping one of the remote sites I get:

**64 bytes from server.fortheloveoffoodblog.com (192.163.200.73): icmp_req=5 ttl=50 time=158 ms**

when I ping this site from her machine I get:

**From lizubuntu.local (192.168.1.100) icmp_seq=20 Destination Host Unreachable**

my thoughts are something(s) on her machine is blocking this url - but what could it be?

---

### Post by steeldriver on 2013-11-26
Possibly her machine has its netmask set such that it is looking for **192**.163.200.73 on the LAN (e.g. 255.0.0.0 instead of 255.255.255.0) - what does the command 

```
route -n
```

say on each machine?

---

### Post by Quarkrad on 2013-11-26
You were right - many thanks.   When I recently changed our routers address I put my wife's details down as 255.0.0.0.  Is there somewhere you could recommend me to read about 255.0.0.0 v 255.255.255.0?  I am interested why certain addresses seemed to be ok but others not.

---

### Post by The Cog on 2013-11-26
For a start, please post the whole ping command and response. We can't tell from the censored posts above whether DNS is even giving the same answers for both machines.

It really makes a difference to post everything - sometimes the problem is just a typing error in the command (not that I'm suggesting it is in this instance).

---

