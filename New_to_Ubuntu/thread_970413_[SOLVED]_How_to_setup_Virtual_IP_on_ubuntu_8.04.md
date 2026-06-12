---
title: "[SOLVED] How to setup Virtual IP on ubuntu 8.04"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by serpent_slang on 2008-11-04
Hi, i am new to Ubuntu, i want to now, how can i have Virtual IP on Ubuntu. 

Scenario is: 

I have 2 machines with Ubuntu installed. The IP of Machine 1 is "192.168.1.20" and Machine 2 is "192.168.1.21". Now what i want to do is to have a virtual IP "192.168.1.22" so that i can communicate with but machines using this IP. 

Can anyone help me, with it.

Regards,
Owais

---

### Post by serpent_slang on 2008-11-04
Hi, i am new to Ubuntu, i want to now, how can i have Virtual IP on Ubuntu. 

Scenario is: 

I have 2 machines with Ubuntu installed. The IP of Machine 1 is "192.168.1.20" and Machine 2 is "192.168.1.21". Now what i want to do is to have a virtual IP "192.168.1.22" so that i can communicate with but machines using this IP. 

Can anyone help me, with it.

Regards,
Owais

---

### Post by hyper_ch on 2008-11-04
why do you want another IP?

---

### Post by overdrank on 2008-11-04
Please do not make multiple threads on the same issues. Threads merged.
:)

---

### Post by wizard10000 on 2008-11-04
> **serpent_slang said:**
> ...Now what i want to do is to have a virtual IP "192.168.1.22" so that i can communicate with but machines using this IP.

Hi, Owais -

I think you meant communicate with *both* machines using this IP.  I'm afraid that's not possible as you can't assign one IP address to more than one MAC address on the same network.

---

### Post by Peter09 on 2008-11-04
You might get a solution to this problem if you could clarify exactly what you want to do. As already said, an IP address cannot exist on two machines at the same time (done that, do not want to do it again - on a large network its a sod to debug).

---

### Post by wizard10000 on 2008-11-04
> **Peter09 said:**
> ...(done that, do not want to do it again - on a large network its a sod to debug).

I think everyone gets to learn this the hard way  ;)

On my networks (home and office) all static IPs are assigned by MAC reservation on the DHCP server rather than on the workstation.  That way I can keep track of stuff like this  ;)

---

### Post by Peter09 on 2008-11-04
Same here, static IP's assigned by DHCP, and only where necessary.

---

### Post by serpent_slang on 2008-11-04
I want to implement the concept of Virtual IP. For more information on Virtual IP please see: [http://en.wikipedia.org/wiki/Virtual_IP_address](http://en.wikipedia.org/wiki/Virtual_IP_address)

I want to know, is there any way to implement this concept in Ubuntu?

---

### Post by TyTiger on 2008-11-04
As far as communicating goes, they are on the same network and both configured correctly so they should be able to communicate across your local network.

i guess you looking in to a server configuration of sorts having read the wiki, No idea :/

---

### Post by Peter09 on 2008-11-04
Ahh - see where you are coming from. 

This is normally used where a device called a load balancer is configured to serve across two or more machines.  The IP address that the user sees is actually the load balancer, it then translates the IP address of the user interface into an IP address of one of the machines that it is using to balance the load. The user sees one machine, but really there are many.

More sophisticated multiple load balancers can work across a single IP. So if you want to spend a few thousand pounds/dollars etc then yes you can.

---

### Post by Sarmacid on 2008-11-04
Really easy to assign a virtual ip(assuming your real interface is th0)```
sudo ifconfig eth0:0 <ip> netmask <netmask>
``` But if you're looking into the load balancer, I don't think this is the way to go.

---

### Post by serpent_slang on 2008-11-04
Yes with the help of a load balancer we can do it. Is there any free load balancer available, so that i can work on it.

---

### Post by Peter09 on 2008-11-04
the phrase 'wishful thinking' comes to mind.:p

---

### Post by serpent_slang on 2008-11-05
Thanks for the tip sarmacid!! 

The solution is similar to HAProxy. [http://www.howtoforge.com/high-availability-load-balancer-haproxy-heartbeat-debian-etch-p2](http://www.howtoforge.com/high-availability-load-balancer-haproxy-heartbeat-debian-etch-p2)

Anyone who is interested in solution can email me. 

Regards,

Owais

---

