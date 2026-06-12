---
title: "minimal cd internet help"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by marine63 on 2008-04-25
hello when I was trying to install the minimal ubuntu on my computer it wouldnt connect to the internet. Also, i have the same problem with unetbootin.

---

### Post by wtp00 on 2009-07-21
Are you using wireless or ethernet?

---

### Post by powel212 on 2009-07-21
First we want to test to make sure the internet is available through your built in Network card. If you can first boot from a live cd and see if you can access the internet. 

I have used the minimal install disc before on machines with old busted network hardware and what I did was buy a $10 Dollar USB-Ethernet device. A great and cheap tool when working on older laptops.

Is your internet PPPOE?

Powel

---

### Post by amusis on 2012-06-16
ok, problem : i want to install ubuntu mini on an old pc but i have a pppoe connection.
i have try 2 road:
1- pppoeconf: but i have this problem[FONT=monospace] 
[/FONT]```
/usr/sbin/pppoeconf : line 523: can't create tmp.xxxxxxxxx: nonexistent directory
cat: can't open 'tmp.xxxxxxx/tmp.yyyyyy' : no such file or directory
```2- pon provider: but i can ping google or other
```
un 16 11:50:39 kernel: [  589.749787] NET: Registered protocol family 24
Jun 16 11:51:01 pppd[2665]: Plugin rp-pppoe.so loaded.
Jun 16 11:51:01 pppd[2667]: pppd 2.4.5 started by root, uid 0
Jun 16 11:51:02 pppd[2667]: PPP session is 5670
Jun 16 11:51:02 pppd[2667]: Connected to 00:19:55:31:e5:48 via interface eth0
Jun 16 11:51:02 pppd[2667]: Using interface ppp0
Jun 16 11:51:02 pppd[2667]: Connect: ppp0 <--> eth0
Jun 16 11:51:02 net/hw-detect.hotplug: Detected hotpluggable network interface ppp0
Jun 16 11:51:02 pppd[2667]: PAP authentication succeeded
Jun 16 11:51:02 pppd[2667]: peer from calling number 00:19:55:31:E5:48 authorized
Jun 16 11:51:02 pppd[2667]: not replacing existing default route via 192.168.1.1
Jun 16 11:51:02 pppd[2667]: local  IP address 79.42.102.221
Jun 16 11:51:02 pppd[2667]: remote IP address 192.168.100.1
Jun 16 11:51:02 pppd[2667]: primary   DNS address 85.37.17.50
Jun 16 11:51:02 pppd[2667]: secondary DNS address 85.38.28.76
```i have added packages 1 by 1 to have pppoe and pon work, maybe i miss 1 or 2 packages.
so i ask 1- what is this error? and 2- if it say i am connected why i can ping out(i can ping router and other pc in lan)?
tnx

---

### Post by overdrank on 2012-06-16
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

