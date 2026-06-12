---
title: "intranet"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-23
Hi,

How do i set up an intranet using static ips?I've got 3 PCs with ubuntu on it and a switch...

Thanks in advance..

Cheers
Davis

---

### Post by Zulu-Zeffir on 2008-06-23
Provide more detail on what you are trying to accomplish.  You could set static addresses on each ubuntu client via editing /etc/network/interfaces file.  You could also set one ubuntu client up as a dhcp server to lease addresses to your other machines.  But again, you need to provide more detail on what you are trying to accomplish.

See this for editing interfaces file:
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html")

---

### Post by ub007 on 2008-06-23
All I wish to accomplish is an intranet,so basically anything works with me.I just thought of going with static ips cz i got confused with all the dhcp dns stuff....however guess the dhcp method would be perfect if thats simple to implement....thanks

b)either way(dhcp or static ips),will it work if i just plug in the 3 PCs into a switch or will i have to configure the switch as well?

---

### Post by Rocket2DMn on 2008-06-23
DHCP should work automatically through your router, which acts as the DHCP server.  It also automatically forwards the DNS information to your computers, so you shouldn't have to worry about that.
You don't have to do any configuration whatsoever for DHCP to kick in, if you wire up or connect to your wireless network, it should automatically assign you an IP.

---

### Post by Zulu-Zeffir on 2008-06-23
I didn't see any mention of a router or wireless.

---

### Post by Rocket2DMn on 2008-06-23
> **Zulu-Zeffir said:**
> I didn't see any mention of a router or wireless.

It is not unusual for posters to exclude information or misname something.  In all likelihood his "switch" is actually a router, not just a switch.  If I am incorrect, please say so ub007.  Perhaps you can tell us what type of networking device you are using (make/model)?

---

### Post by hovzio on 2008-06-23
> **Rocket2DMn said:**
> It is not unusual for posters to exclude information or misname something.  In all likelihood his "switch" is actually a router, not just a switch.  If I am incorrect, please say so ub007.  Perhaps you can tell us what type of networking device you are using (make/model)?

I think his other post sums it up:

[http://ubuntuforums.org/showthread.php?t=838571](http://ubuntuforums.org/showthread.php?t=838571)

---

### Post by Rocket2DMn on 2008-06-23
Thanks for the find hovzio, I will request to the mods that his other thread be moved to the Networking forum since it is unlikely to get good help here.

---

### Post by ub007 on 2008-06-23
ooppsss,

sorry for the confusion....
my supervisor asked me to unplug the server from the uni n/w if dhcp is started on it and thats y he provided me with the switch(havent done any configuration on it)....however i cant access the internet if i unplug from the uni n/w n also tryn to find an alternative to accomplish both tasks...i thought bout static ips,but curious to tweak dhcp to find a solution.....
I'll paste this in the n/w forum..thanks

cheers

---

### Post by Zulu-Zeffir on 2008-06-24
> **Rocket2DMn said:**
> It is not unusual for posters to exclude information or misname something.  In all likelihood his "switch" is actually a router, not just a switch.  If I am incorrect, please say so ub007.  Perhaps you can tell us what type of networking device you are using (make/model)?

Good point.

---

### Post by ub007 on 2008-06-27
thanks guys,i was able to figure that out....cheers

---

### Post by Xiong Chiamiov on 2008-06-27
Whenever you figure something out, it's nice if you post what you did to get things working for those who come across this thread later.

---

### Post by ub007 on 2008-06-27
Sorry mate...it was pretty simple,so thought I was kinda naive to ask that question in the first place....anyways heres what i did

- plug in the 3 PCs into the switch
-assign static IP to the server (sudo nano /etc/network/interfaces-configure this file)
-install and configure dhcp server on the same PC(ask if configuration help needed)
-on the client PCs:edit /etc/network/interfaces(change from static to dhcp,tag the rest)then $sudo /etc/init.d/networking restart
$sudo dhclient

-viola done....,in case anyone needs the configuration in more detail plz ask.

Cheers

---

