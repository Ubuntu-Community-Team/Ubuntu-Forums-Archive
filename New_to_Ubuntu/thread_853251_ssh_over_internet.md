---
title: "ssh over internet"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Inxsible on 2008-07-08
I have successfully setup ssh on my Debian install and I can ssh to my heart's content within the LAN.

I use putty and winscp to connect from my windows machine.

How would I setup an access over the internet? I created an account at dyndns.org from that machine, but when I try to access it, it just fails and gives me ```
Network error: Connection timed out
```What else do I have to do in order to get this working?

Some details:
The host has a local static IP address through a router : 192:168.x.x
But my ISP gives a dynamic IP address.

Let me know if you need anymore information

---

### Post by jamesrfla on 2008-07-08
You need to forward port 22 or if you changed the default port number port forward that port number.

---

### Post by Inxsible on 2008-07-08
> **jamesrfla said:**
> You need to forward port 22 or if you changed the default port number port forward that port number.I should have mentioned... I have already forwarded my port

---

### Post by jamesrfla on 2008-07-08
I think I had the some problem except for different protocol. Got to [http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html) and test the port.

---

### Post by jamesapnic on 2008-07-08
try running netcat on the port

nc -l -p 22, connect remotely using telnet and type something, if you dont see something then the chances are either the Ubuntu box is firewalling it or it is not forwarded properly on your router.  On Ubuntu use iptables -I INPUT -j ACCEPT -p tcp --dport 22 to allow it through.  On your router it will depend on the model.

---

### Post by Dr Small on 2008-07-08
First synopsis, let's go over all the basics before we have to go too technical :)

SSHd must be running on the [system] that you are SSHing into.
[If SSHd running on port 22] port 22 must be open on your [system] firewall [if you have one].
[If you are behind a router] Port 22 must be forwarded to the [system]'s IP address.
On your DynDNS account, it must be pointing to your [external] IP.

In your ssh client [putty] connect to your DynDNS account address on port 22.
If possible, port scan your DnyDNS account and make sure port 22 is visibly open.

---

### Post by Inxsible on 2008-07-08
> **Dr Small said:**
> First synopsis, let's go over all the basics before we have to go too technical :)

SSHd must be running on the [system] that you are SSHing into. [COLOR=Red]Check[/COLOR]
[If SSHd running on port 22] port 22 must be open on your [system] firewall [if you have one].[COLOR=Red] its not on port 22...and my firewall has it open .Check[/COLOR]
[If you are behind a router] Port 22 must be forwarded to the [system]'s IP address. Check
On your DynDNS account, it must be pointing to your [external] IP.[COLOR=Red]Check[/COLOR]

In your ssh client [putty] connect to your DynDNS account address on port 22. [COLOR=Red]Check[/COLOR]
If possible, port scan your DnyDNS account and make sure port 22 is visibly open.[COLOR=Red]Will do this[/COLOR]


See my replies in red

---

### Post by Inxsible on 2008-07-08
I shall try out both james' suggestions later tonight.

---

### Post by Dr Small on 2008-07-08
Also, this is rather trivial, but just to make sure for certain, I would like to ask this question.
In your router, do you have port 22 forwarded to [system] on whatever port you are running SSHd on?

So, if [system] is running on port 888 with an IP of 192.168.0.100 for example, in your router you would forward port 22 to port 888 on 192.168.0.100.

As I said, it is very trivial, but I just wanted to make sure. Take care, and I hope you get the problem solved soon :)

Dr Small

---

### Post by Inxsible on 2008-07-08
> **Dr Small said:**
> Also, this is rather trivial, but just to make sure for certain, I would like to ask this question.
In your router, do you have port 22 forwarded to [system] on whatever port you are running SSHd on?

So, if [system] is running on port 888 with an IP of 192.168.0.100 for example, in your router you would forward port 22 to port 888 on 192.168.0.100.

As I said, it is very trivial, but I just wanted to make sure. Take care, and I hope you get the problem solved soon :)

Dr SmallThanks for the tips. all great to be sure of diagnosing the problem correctly.

I do have the port forwarded to the correct IP of the machine that I want to ssh into.

---

### Post by wigren on 2008-08-05
Was there ever a resolution to this? I'm having the same issue. I've gone over Dr Small's checklist and every thing checks out, including scanning my DynDNS account and finding port 22 open and accepting connections. However, when I ssh to either my DynDNS host or my external IP it either times out (GUI, using the Connect to Server tool) or instantly replies "ssh: connect to host [IP address or DynDNS host] port 22: Connection refused" (CLI). I can ssh over the LAN and to a friend's server, but not to my desktop.

---

