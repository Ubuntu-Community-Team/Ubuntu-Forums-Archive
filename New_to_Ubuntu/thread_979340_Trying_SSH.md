---
title: "Trying SSH"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by I am &gt;= Wes on 2008-11-11
I'm trying to use ssh.  It seems kind of cool, but I don't really need it.  I'm just kind of doing this to learn for my own sake.  I'm trying to connect to my dad's mac and I have the box checked in "sharing" and everything so it should work.  At the bottom of the window it tells me what to type in to connect to it remotely.
```
ssh usrname@internalip
```
It gives me the user name and the internal ip, but it doesn't seem to work.  I'd really like to get this to work.
Suggestions?

--Wes

---

### Post by jimmy the saint on 2008-11-11
try installing Putty.
[code]sudo apt-get update[\code]
[code]sudo apt-get install putty[\code]
and connecting with it.  Also, I don't know much about macs, but is an ssh server active on the mac?

---

### Post by iponeverything on 2008-11-11
What does it do when you try to connect?

can you ping the other ip address?

---

### Post by I am &gt;= Wes on 2008-11-11
When I try to connect I get "conection refused".  I don't know if about the ssh server on the mac, it should be up, but I know I have one up on this machine and it doesn't work from the mac to this one (same output).  How do I ping?

Putty also tells me "connection refused."

---

### Post by jimmy the saint on 2008-11-11
```
ping "ip address"
```
without the quotes

---

### Post by iponeverything on 2008-11-11
ping <ipaddress>

to ping 
connection refused sounds like the mac is not listening

---

### Post by ghost_ryder35 on 2008-11-11
> **I am >= Wes said:**
> When I try to connect I get "conection refused".  I don't know if about the ssh server on the mac, it should be up, but I know I have one up on this machine and it doesn't work from the mac to this one (same output).  How do I ping?
connection refused means A. the firewall on the MAC refused your connection, or B. the service on the MAC is not running so the connection was refused

---

### Post by I am &gt;= Wes on 2008-11-11
When I ping the ip address I get "destination port unreachable" continuously.

I configured the firewall to allow ssh, I think.

---

### Post by ghost_ryder35 on 2008-11-11
if you cant ping it you have even bigger problems.  what are your internal ip addresses?

---

### Post by I am &gt;= Wes on 2008-11-11
This machine is 192.168.2.2 and the mac is 192.168.1.2

---

### Post by ghost_ryder35 on 2008-11-11
> **I am >= Wes said:**
> This machine is 192.168.2.2 and the mac is 192.168.1.2
how is the network setup?  currently they are on two diffrent subnets, and if the router does not know about the other network its not going to route... do you have two routers?

---

### Post by I am &gt;= Wes on 2008-11-11
Yea I do.  that might explain a lot actually.

So is there a way I can fix it? I mean, while keeping one router.

---

### Post by ghost_ryder35 on 2008-11-11
you'll have to configure routes on the routers so they know where to forward the traffic.  also make sure the networks do not overlap on each router.

---

### Post by handydan918 on 2008-11-11
> **ghost_ryder35 said:**
> you'll have to configure routes on the routers so they know where to forward the traffic.  also make sure the networks do not overlap on each router.

Or maybe even more simply, eliminate one router, and replace it with a <20$ hub....

---

### Post by I am &gt;= Wes on 2008-11-11
How should I go about doing that?

I don't really want to spend money on this so the hub is out, sorry.

---

### Post by ghost_ryder35 on 2008-11-11
just use one router, on one subnet assuming you have open cat5e ports on one of the routers built in switches.

---

### Post by handydan918 on 2008-11-11
> **ghost_ryder35 said:**
> just use one router, on one subnet assuming you have open cat5e ports on one of the routers built in switches.

Ummm, yes, "assuming you have open cat5e ports", but if that were the case, who would use 2 routers?

---

### Post by ghost_ryder35 on 2008-11-11
> **handydan918 said:**
> Ummm, yes, "assuming you have open cat5e ports", but if that were the case, who would use 2 routers?
> **I am >= Wes said:**
> had to put text here *ghost_ryder35*

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
the arrows are pointing UP

---

