---
title: "Slow ssh speed (login is fast)"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-10-05
I run a openssh server on my desktop and when I want to transfer something to my laptop, the speed if very slow.

It ranges from 500kb/s (!!!!!) to 1.1mbit/sec.

I should get speeds to 10mbit.

I used to get these speeds over ssh, but for some reason it doesn't anymore.

The whole reason I have ssh is so I can quickly move big files so I don't need to use flash drives. 

Now 700mb takes around 20 minutes to transfer, that is way too long.

Any ideas as to why this is happening?

--

In the title I say the login is fast, because when googling this problem almost all posts were about slow logins. This is not the case here.

---

### Post by schwascore on 2008-10-05
is this a wired or wireless connection?

---

### Post by ZxEfR on 2008-10-05
Yeah 500mb takes 30 minutes for me. 300KB/sec on my lan!  :(

Also used to be a lot faster. I'm running Intrepid on the desktop now maybe that has something to do with it. Hardy is on the laptop. Tried going either direction and it's the same speed.

I'm running a wired connection via a router.

I'm doing the google search thing too and yeah everything is about login speed not transfer speed.

EDIT: Now (the next day) it's creeping on down to 170KB/sec. I'll be gone for the next 3 or 4 days but any help would be appreciated. Thanks.

---

### Post by billgoldberg on 2008-10-06
I going to need to bump this.

--

Additional info.

My laptop connects to the router over wifi.

The server is running on my desktop, that attached's to the router by an ethernet cable.

---

### Post by billgoldberg on 2008-10-07
Bump.

---

### Post by SomethingCronic on 2008-10-08
Probably unrelated, but recently my desktop has been slowing down a lot - particularly when I SSH into the box from work.

Checking /var/log/auth.log I found I was being bombarded by bots trying to enter my system using the ssh port.

If you leave your ssh open to the net, I would suggest using a different port number (2277?) so that these opportunists won't try to attack.

Even though this may not resolve your problem, I would generally suggest this anyway to everyone.

---

### Post by billgoldberg on 2008-10-08
> **SomethingCronic said:**
> Probably unrelated, but recently my desktop has been slowing down a lot - particularly when I SSH into the box from work.

Checking /var/log/auth.log I found I was being bombarded by bots trying to enter my system using the ssh port.

If you leave your ssh open to the net, I would suggest using a different port number (2277?) so that these opportunists won't try to attack.

Even though this may not resolve your problem, I would generally suggest this anyway to everyone.

I'll try a different port.

---

### Post by Cpuboye11 on 2008-10-08
Do you have any of the Firewall or any kind of VPN software installed either then the SSH Server on your desktop or laptop... Also opening ports off your router will only open that machine to the Internet... All ports are open on the local lan. Just saying...

---

### Post by billgoldberg on 2008-10-08
> **Cpuboye11 said:**
> Do you have any of the Firewall or any kind of VPN software installed either then the SSH Server on your desktop or laptop... Also opening ports off your router will only open that machine to the Internet... All ports are open on the local lan. Just saying...

I know.

I had my iptables configured to allow all traffic on port 22.

I will test the ssh connection again with the new port in a while. Hope it works but I don't really think so.

---

### Post by Nxion on 2008-10-08
Another thing that you can try (maybe you have already) is to uninstall and purge SSH from both boxes and reload. I have done this in the past and this has resolved my issue. Hope that helps.

---

### Post by billgoldberg on 2008-10-08
> **Nxion said:**
> Another thing that you can try (maybe you have already) is to uninstall and purge SSH from both boxes and reload. I have done this in the past and this has resolved my issue. Hope that helps.

Should changing the ports won't work, I'll purge and reinstall.

---

