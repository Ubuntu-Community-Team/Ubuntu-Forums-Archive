---
title: "Lost in network land"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by erdomi on 2008-08-27
I've just spent several hours wading through old posts and seem to be getting nowhere.  Hoping someone can help:

Here's the summary:

I can ping to localhost and nowhere else.
I can ssh to myself only.
I can ftp to outside places just fine.
I can surf the internet just fine.
VPNC doesn't seem to work.

Trying to ping to bu.edu gives me:
ping: sendmsg: Operation not permitted

Trying to ssh to the outside world just sits for a while before telling me that the connection timed out.


VPNC gives me:
```
sh: /etc/vpnc/vpnc-script: Permission denied
sh: /etc/vpnc/vpnc-script: Permission denied
VPNC started in background (pid: 13914)...

```

Don't really know what I'm doing with firewalls. I tried allowing port 22 with:

```
sudo ufw allow 22/tcp

```

I tried installing firestarter and configuring using [this link]("http://74.125.95.104/search?q=cache:HjE9Qq_XevUJ:www.howtoadvice.com/FirestarterVPN/+configure+firestarter+vpnc&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")

Nothing seems to work.  Any help is greatly appreciated.

---

### Post by hubie on 2008-08-27
It sounds like a firewall issue to me.  I wonder if you have any other firewalls running that you are not aware of?

[Here]("http://www.codemonkies.co.nz/linux/2008/05/25/ping-sendmsg-operation-not-permitted/") is something to look at.

---

### Post by erdomi on 2008-08-28
Thank's very much for the reply, hubie.  

Let me reemphasize that I really don't know what I'm doing when it comes to firewalls.  

I installed impasq, ran it (sudo impsaq) and it seemed to do nothing (all above mentioned symptoms are the same).  The man page and documentation mean to this nothing to me.  What is it supposed to do?

How do I check to see what iptables script or config I may be running?

How do I check to see what interface I am using and what interface my scripts think I'm using?

Thanks!

---

### Post by brian_p on 2008-08-28
> **erdomi said:**
> 

Nothing seems to work.  Any help is greatly appreciated.

Remove iptables configuration programs:

```
sudo apt-get remove --purge ufw
```

```
sudo apt-get remove --purge firestarter
```

Do you really need ipmasq?

```
sudo apt-get remove --purge ipmasq
```

Check state of iptables:

```
sudo iptables -L
```

Hopefully it will show:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Test ping etc. Configure other programs to work as you want. Forget about the firewall and enjoy a functioning safe system.

---

### Post by erdomi on 2008-08-28
Thanks for your reply, brian_p.  

I tried all of your suggestions and I seemed to have no problems.  I did get the expected output for 

```
sudo iptables -L
```

Unfortunately, it didn't solve any of my problems.  VPNC, ssh, ping still don't work.

Any other suggestions?

---

### Post by brian_p on 2008-08-28
> **erdomi said:**
> 

Any other suggestions?

Any other machines on your network? Do they respond to ping?

bu.edu has an IP of 128.197.27.7.

```
ping 128.197.27.7
```

Does that work?

Do you have a router? Does it have a firewall blocking outgoing ICMP packets?

---

### Post by nicedude on 2008-08-28
For configuring your built in linux iptables firewall I would recommend guarddog over firestarter as I found it much easier to use and it works great for me. Its in the repositories so you should be able to find it easy.

---

### Post by bicyclebarron on 2008-08-28
Check your router configuration. Most need to be configured to allow VPN. Also make sure you have the correct app for your VPN.

---

### Post by erdomi on 2008-08-28
Thanks for the replies!

I hadn't even thought about my router's firewall.  I changed my router firewall configuration to low security and this seemed to fix my ping and ssh problems.  yeah!!!

so yes, ```
ping 128.197.27.7
``` works now.

thanks for the guarddog suggestion.  I will try that.

so still my vpnc problem persists. How do I configure my router to allow vpn?  (My router is hooked up to my husband's computer running windows XP.)

Also, how do i know what the correct app is?  I've used vpnc successfully before on previous ubuntu installs the same way I am trying to use it now.

Thanks a lot for your posts!

---

### Post by cariboo on 2008-08-29
You should make sure you have port 500 forwarded from your computer to the router. You will have setup port forwarding on your router, to do this you will have to access the administration page in your router, because there are so many different routers out there I would suggest checking the documentation for the routers ip address.

Jim

---

### Post by brian_p on 2008-08-29
> **erdomi said:**
> 

thanks for the guarddog suggestion.  I will try that.

Your need to alter the present iptables rules with guarddog or any other program is zero if for no other reason that you are behind a router.

> so still my vpnc problem persists. How do I configure my router to allow vpn?  (My router is hooked up to my husband's computer running windows XP.)

vpnc is a client program; it sends packets out and receives responses. Forwarding ports on the router to the computer is not going to help.

A non-working vpnc could be due to an incorrect set up of the program or a router configuration related to outgoing packets.

> Also, how do i know what the correct app is?

That depends on what you want to do.

---

