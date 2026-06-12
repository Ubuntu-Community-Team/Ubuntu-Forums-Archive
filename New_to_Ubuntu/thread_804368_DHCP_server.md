---
title: "DHCP server"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by x88a on 2008-05-23
i know what a DHCP server is.
My question is, how is it applicable in real life?
what can one do with a DHCP server?
Can someone give me some examples?
TQ

---

### Post by Helios38 on 2008-05-23
the DHCP server is very useful. it is integrated in most routers, allowing automatic assignment of IP's to networked computers, meaning less configuration.




lets say i have a router in which i have 5 computers connecting to it. i could go through all the trouble of having each computer registered with an IP address, which is really annoying to do, or i can have DHCP do it for me

:)

---

### Post by mapes12 on 2008-05-23
A DHCP service between you and the internet will cloak your private address (assigned by DHCP to your client machine) via Network Address Translation (NAT) to the public IP address assigned to you by your ISP and which you are broadcasting across the web. Thus making you far more secure than broadcasting a public IP address straight from your PC.

Additionally, by default the Ubuntu setup installation will look for a DHCP service within your local network. If one isn't there then Ubuntu will not setup network services. You will then have a hell of a time trying to access the internet or any other LAN clients.

---

### Post by x88a on 2008-05-23
so if 2 comps are connected through DHCP, it means they both can communicate?

Eg:-
1. they both can play games together.
2. They both can serve internet together with 1 comp taking the internet connection from the other comp.
3.  They can transfer files among each other.

Am i right?

---

### Post by StOoZ on 2008-05-23
When you deploy Dynamic Host Configuration Protocol (DHCP) servers on your network, you can automatically provide client computers and other TCP/IP-based network devices with valid IP addresses. You can also provide the additional configuration parameters these clients and devices need, called DHCP options, that allow them to connect to other network resources, such as DNS servers, WINS servers, and routers.

---

### Post by cwgatling on 2008-05-23
Technically, a single DHCP server can assign addresses to multiple subnets. However, I think in your case (probably a router acting as DHCP server) your 2 computers are in the same subnet meaning that the answer to all your questions is 'yes'.
The question about using 1 computer as a gateway to the Internet is interesting because DHCP is not the best solution for that in my opinion. I'd be looking at static addresses for that scenario.
BTW, DHCP and NAT can work completely independently of each other.

---

### Post by mapes12 on 2008-05-23
> so if 2 comps are connected through DHCP, it means they both can communicate?

Eg:-
1. they both can play games together.
2. They both can serve internet together with 1 comp taking the internet connection from the other comp.
3. They can transfer files among each other.

Am i right?

Yes to everything. Additionally, you would not have to drop the internet connection on one machine for another to access the web. A DHCP router can handle many machines accessing the internet at the same time.

---

### Post by fmpfmpf on 2008-05-23
this is interesting
i am trying to create a DHCP server so that both laptops can serve the internet together.
can you guys plsss help me?
[http://ubuntuforums.org/showthread.php?t=804380](http://ubuntuforums.org/showthread.php?t=804380)

thank you

---

