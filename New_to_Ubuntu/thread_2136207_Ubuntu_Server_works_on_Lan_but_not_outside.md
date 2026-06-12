---
title: "Ubuntu Server works on Lan but not outside"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by saponempotenti on 2013-04-16
My Ubuntu server can be accessed on the LAN, but not the WAN.  I have been able to gain access to the server with sftp and ssh, but again only if the said machine trying to get access is on the LAN.  While attempting to view the webpage or ssh into the server from outside the LAN it times out every time.  I have set up port forwarding.  Not sure as to what I could be missing.  Is there something on the actual server that I need to setup or manage?

---

### Post by papibe on 2013-04-16
Hi saponempotenti.

Before troubleshooting I just want to make sure that you actually are trying to access your server from outside your network, and not from inside but using public IP. Most routers won't allow that. If you are using your phone or tablet 3G service, make sure they are disconnected from your WiFi.

Regards.

---

### Post by alphacrucis2 on 2013-04-16
First make sure the server has a default route specified that points at the WAN router. What do you get from

```
ip route list
```


As papibe said you may also need to set up port forwarding on your router for outside things to connect in.

---

### Post by steeldriver on 2013-04-16
another thing to check is that you don't have a firewall rule on the server that is restricting ALLOW addresses to your LAN IP range

---

### Post by saponempotenti on 2013-04-17
> **papibe said:**
> Hi saponempotenti.

Before troubleshooting I just want to make sure that you actually are trying to access your server from outside your network, and not from inside but using public IP. Most routers won't allow that. If you are using your phone or tablet 3G service, make sure they are disconnected from your WiFi.

Regards.

I have tried from several machines outside the network as well as my phone with 4g :(

---

### Post by saponempotenti on 2013-04-17
> **alphacrucis2 said:**
> First make sure the server has a default route specified that points at the WAN router. What do you get from

```
ip route list
```


As papibe said you may also need to set up port forwarding on your router for outside things to connect in.

paulson@ProQuaerendumScientiam:~$ ip route list
default via 192.168.1.1 dev eth1  metric 100
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.111

As I am fairly new to linux I am not sure how to interpret that :/

---

### Post by saponempotenti on 2013-04-17
> **steeldriver said:**
> another thing to check is that you don't have a firewall rule on the server that is restricting ALLOW addresses to your LAN IP range

While attempting to fix the issue I thought of that and completely removed shorewall, but still no luck.

---

### Post by steeldriver on 2013-04-17
I'm not a routing expert but that looks OK to me (mine is analogous - assuming 192.168.1.1 is your router/gateway and 192.168.1.111 is the machine's LAN IP)

It still may be worth a quick check on firewall status - since other tools can mess with iptables let's look right down at that level if possible e.g.

```

$ sudo iptables -L | grep -E 'dpt:((ssh)|(http))'

$ sudo ufw status numbered

```

---

### Post by Hadaka on 2013-04-17
Hi, ssh is a little confuseing when you are new to it.
let's see if we can remove some of the mystery.

to ssh inside the lan...you enter  -> ssh -p (port#) user@ip address
                                                 ssh -p  22 aname@192.168.1.8 <-example

to ssh from OUTSIDE you enter  -> ssh -p (port#) user@ROUTER ip
                                                 ssh -p  22 aname@75.100.22.39 <-example

*To find Your ROUTER IP ..from a browser connection enter -> canyouseeme.org
this will display YOUR ROUTER IP

* BEFORE you can connect from outside the lan you MUST portforward  your port (22) example to your lan ip.

*example..in router port forwarding settings. -> start 22 end 22 ip 192.168.1.8
*read your router manual on HOW TO PORT FORWARD..
*note ssh to router ip from INSIDE the lan does NOT work.
hope this helps.

*edit: didnt see your attachment till after i posted. oh well..

---

### Post by saponempotenti on 2013-04-17
After reading all the advice (steel driver, your commands just caused the terminal to hang so was slightly confused about that) I am pretty sure the cause of the problem is my router blocking all incoming requests.  Would that make sense with the situation?

---

### Post by alphacrucis2 on 2013-04-17
> **saponempotenti said:**
> After reading all the advice (steel driver, your commands just caused the terminal to hang so was slightly confused about that) I am pretty sure the cause of the problem is my router blocking all incoming requests.  Would that make sense with the situation?

You do have port forwarding configured on your router right? That is the only way to get from a public internet address to an internal private RFC type address such as 192.168.1.111

---

### Post by papibe on 2013-04-17
Check if your ISP is blocking the port you're using. Check it here: [canyouseeme.org]("http://www.canyouseeme.org/").

Sometimes low standard ports like 22, 25 and 80 are blocked. If that your case, changing the port to a higher value, specially on the dynamic range (49152&#8211;65535), would solve this.

If your server set to use a DHCP reservation, or an static IP?

Let us know how it goes.
Regards.

EDIT: removed port trigger part.

---

### Post by saponempotenti on 2013-04-17
> **papibe said:**
> Check if your ISP is blocking the port you're using. Check it here: [canyouseeme.org]("http://www.canyouseeme.org/").

Sometimes low standard ports like 22, 25 and 80 are blocked. If that your case, changing the port to a higher value, specially on the dynamic range (49152&#8211;65535), would solve this.

If your server set to use a DHCP reservation, or an static IP?

Let us know how it goes.
Regards.

EDIT: removed port trigger part.

The server is set to a static IP.  I tired port 81 but will try a higher range as you suggested.  I believe my motherboard failed so it may be a while before I get back to you :'(

EDIT: Was just a graphics card malfunction! Never fixed a computer hardware issue so fast!  Also I tried a higher port (49152) and still got a timeout error :(

---

### Post by CharlesA on 2013-04-17
> **saponempotenti said:**
> The server is set to a static IP.  I tired port 81 but will try a higher range as you suggested.  I believe my motherboard failed so it may be a while before I get back to you :'(

Good luck. My ISP blocks port 80, so I tested my site with port 8080, which is the alternate HTTP port. Worth a shot once you get the machine back up and running.

---

### Post by saponempotenti on 2013-04-17
> **CharlesA said:**
> Good luck. My ISP blocks port 80, so I tested my site with port 8080, which is the alternate HTTP port. Worth a shot once you get the machine back up and running.

Have tried multiple ports that my ISP should not be blocking.. also called the ISP and after talking to a tech, he assured me that there is no port blocking in the first place.  I have scanned the ports on my router as well as on the server and both of them show ssh and http open.  When I send a request to the router from an external machine it gets a timeout error every time though.

---

### Post by CharlesA on 2013-04-18
> **saponempotenti said:**
> Have tried multiple ports that my ISP should not be blocking.. also called the ISP and after talking to a tech, he assured me that there is no port blocking in the first place.  I have scanned the ports on my router as well as on the server and both of them show ssh and http open.  When I send a request to the router from an external machine it gets a timeout error every time though.

If they aren't blocking ports and canyouseeme.org shows them as open, the problem must lie elsewhere.

---

### Post by saponempotenti on 2013-04-18
> **CharlesA said:**
> If they aren't blocking ports and canyouseeme.org shows them as open, the problem must lie elsewhere.

canyouseeme.org does not see them because it gets a time out error

---

### Post by papibe on 2013-04-18
> **saponempotenti said:**
> canyouseeme.org does not see them because it gets a time out error
That could be a sign of blockage, actually.

Did you try ports on the dynamic range?

Another thoughts:
[LIST]
[*]Make sure your static IP is outside the DHCP range of the router.
[*]I would always prefer to set a DHCP reservation, since that way you are sure that the router "knows" the machine.
[/LIST]
Regards.

---

### Post by saponempotenti on 2013-04-18
> **papibe said:**
> That could be a sign of blockage, actually.

Did you try ports on the dynamic range?

Another thoughts:
[LIST]
[*]Make sure your static IP is outside the DHCP range of the router. 
[*]I would always prefer to set a DHCP reservation, since that way you are sure that the router "knows" the machine. 
[/LIST]
Regards.

Ahhhh.. I set up a DHCP reservation and removed the static ip from the server.. its ip is still .111 though.  I have tried a DMZ as well as using a range.  Still has the same issues.

---

### Post by saponempotenti on 2013-04-18
> **steeldriver said:**
> I'm not a routing expert but that looks OK to me (mine is analogous - assuming 192.168.1.1 is your router/gateway and 192.168.1.111 is the machine's LAN IP)

It still may be worth a quick check on firewall status - since other tools can mess with iptables let's look right down at that level if possible e.g.

```

$ sudo iptables -L | grep -E 'dpt:((ssh)|(http))'

$ sudo ufw status numbered

```

```
paulson@ProQuaerendumScientiam:~$ sudo iptables -L | grep -E 'dpt:((ssh)|(http))'
paulson@ProQuaerendumScientiam:~$ sudo ufw status numbered
Status: inactive
paulson@ProQuaerendumScientiam:~$ 
```

Should the status be inactive?

---

### Post by CharlesA on 2013-04-18
Yes, it should be inactive because you haven't enabled ufw. :)

As far as I can tell no firewall is enabled and unless your port forwarding setup is incorrect, it should "just work"

---

### Post by saponempotenti on 2013-04-18
> **CharlesA said:**
> Yes, it should be inactive because you haven't enabled ufw. :)

As far as I can tell no firewall is enabled and unless your port forwarding setup is incorrect, it should "just work"

Well I am at a loss, going to try another router tomorrow. Thanks for the help

---

### Post by saponempotenti on 2013-05-24
> **saponempotenti said:**
> Well I am at a loss, going to try another router tomorrow. Thanks for the help

Well a new modem fixed the problem.  Apparently my modem was actually a modem/router and it was broken.. after having a friendly cable technician fix the cable signal and replace the modem with one that actually worked, my server is now up and running on the WAN! :D

Thanks to everyone that helped!

---

