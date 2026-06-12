---
title: "Virtual IPs"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by ub007 on 2008-08-05
I just edited my post after the lab session.so here it is....Appreciate if anyone could help me out here....

I have set up virtual IPs on my Ubuntu client machine & assigned IPs 192.168.12.3 - eth0
192.168.12.4 - eth0:1
192.168.12.5 - eth0:2
192.168.12.6 - eth0:3

When I access the website on my intranet server & check the logs on the apache server ,i find that the HTTP 'GET' request is sent from the client IP 192.168.12.3.Is there any way that I can send the http requests from the other IPs on the virtual interfaces.

So if i were to put it in a loop using a perl/python script,i could possibly send 'get' requests randomly from the virtual IPs and the log file on the server would reflect that......Appreciate if anyone could provide some ideas on this,or am i completely naive here..

CHeers
David

---

### Post by ub007 on 2008-08-06
does it make sense moving this thread to the 'networking topic'?

---

### Post by y@w on 2008-08-06
Check out this article: [http://en.wikipedia.org/wiki/Virtual_IP_address](http://en.wikipedia.org/wiki/Virtual_IP_address)

Specifically the first sentence: "A virtual IP address (VIP or VIPA) is an IP address that is not connected to a specific computer or network interface card (NIC) on a computer. Incoming packets are sent to the VIP address, but all packets travel through real network interfaces."

Evidently this must be difficult. I found one old post from someone trying to do something similar, but not having any luck. It sounds like the machine will just pick the default route and send through that, but I could be wrong.
[http://ubuntuforums.org/showthread.php?t=450576](http://ubuntuforums.org/showthread.php?t=450576)

I've struggled with this before and eventually just gave up.

---

### Post by The Cog on 2008-08-06
Since the virtual interfaces are all on teh same subnet, the computer has no reason to favour any one in particular when making outgoing calls. It is probably just picking the first one in its list. I don't know how you could influence that without doing using an **ip route add ...** command and using the **src** option to set the source address. see **man ip** for details.

The machine will of course accept incoming connections to any of those addresses.

---

### Post by ub007 on 2008-08-06
> Since the virtual interfaces are all on teh same subnet, the computer has no reason to favour any one in particular when making outgoing calls. It is probably just picking the first one in its list. I don't know how you could influence that without doing using an ip route add ... command and using the src option to set the source address. see man ip for details.

That was helpful....Could you plz tell me how to use the src option to set the source address...thats exactly what i need...

> The machine will of course accept incoming connections to any of those addresses.
Yes,it works.....

---

### Post by The Cog on 2008-08-06
I guess the command goes something like:
**ip route add 1.2.3.4 via 192.168.12.1 src 192.168.12.4**
where 1.2.3.4 is the destination,
192.168.12.1 is your default gatewaym and
192.168.12.4 is the address you want to source the connection from.

Or this:
**route add 1.2.3.4 gw 192.168.12.1 dev eth0:1**

---

### Post by ub007 on 2008-08-07
Thanks y@w for the link,it provides some insight ,though not the solution i'm looking for...

Thanks Cog,your reply gave me a clear picture of how it works and will try that out....however i doubt that would solve my problem...I do not wish to set a static outgoing IP,need to script something that would pick a random IP from the list as source.so it would be like in the first attempt,the http get req may come from 192.168.12.3,in the 2nd attempt from 192.168.12.4 and so on.....


Cheers,
David

---

