---
title: "accessing my server from outside my lan"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by moose4204l on 2008-08-13
how do I make my LAMP server accessible to people outsde my lan?

---

### Post by OffAxis on 2008-08-13
You just have to forward port 80 through your router.
Then you can type in the WAN IP and access it directly, or if you have a domain name, you can set up your account (from wherever you registered it) to forward traffic to your WAN IP.

---

### Post by ibutho on 2008-08-13
What type of internet connection to do you have? If you have a router, you need to forward the ports for http (and other services you need) to your webserver. This is usually done via some sort of web interface on your router. Also make sure that if a firewall is running on the server, the ports for http and other services you desire are open.

---

### Post by moose4204l on 2008-08-13
I did. I have netgear and I created a http port. I put the inet addr minus the last digit and inserted .101 with port fowarding to 80. Then I also put my public IP address in the apache2 httpd.conf file. Did I do it wrong/ miss something or what?

---

### Post by Cypher on 2008-08-13
The essential steps
1) Configure Apache to listen on a particualr port, 80 will be abused very quickly, pick something else.
2) Configure your server to have a static IP address in /etc/network/interfaces
3) Configure your router to forward all traffic on your newly defined HTTP port to your PC's static IP address at the newly defined HTTP port.
4) Register with DynDNS or NO-IP to get an URL that you can use from the web.
5) In your DynDNS/No-IP account put in your public IP address you get from your ISP
6) (Optional) Most routers have an option to keep your DynDNS/No-Ip account up to date with the DHCP address your get from your ISP should your router/modem reboot for whatever reason.

Done.

---

### Post by moose4204l on 2008-08-14
> **Cypher said:**
> The essential steps
1) Configure Apache to listen on a particualr port, 80 will be abused very quickly, pick something else.
2) Configure your server to have a static IP address in /etc/network/interfaces
3) Configure your router to forward all traffic on your newly defined HTTP port to your PC's static IP address at the newly defined HTTP port.
4) Register with DynDNS or NO-IP to get an URL that you can use from the web.
5) In your DynDNS/No-IP account put in your public IP address you get from your ISP
6) (Optional) Most routers have an option to keep your DynDNS/No-Ip account up to date with the DHCP address your get from your ISP should your router/modem reboot for whatever reason.

Done.

-- I opened the ports.conf file and added the line ```
Listen 8001
```. Should I delete the Listen 80?

-- How do I set up a static IP address?
  my inet addr is 192.168.0.5
  netstat -r for gateway is 192.168.0.1
  i know my public IP.

I set up all the servers from the CD so I think I have the DNS but I have no clue on how to do that either, i'm taking one step at a time.

---

### Post by moose4204l on 2008-08-14
bump

---

### Post by bgerlich on 2008-08-14
Check if you have a public IP address.

---

### Post by moose4204l on 2008-08-14
i know my public ip address. i put that in the httpd.conf file 

ServerName localhost
ServerName <publc ip addr>

---

### Post by bgerlich on 2008-08-14
So you can connect to your router form outside of your lan and you can connect to your http server form inside of your lan, but not form outside?

Sorry for those questions but the answers will give a clear view of the situation.

---

### Post by cariboo on 2008-08-14
You don't need to put public ip address any where in any configuration files on your server, as your server is not directly connected to the internet. Restore your configuration files to their origional state, and do as previous posters have said. Set up a static ip address for your server and set up port forwarding in your router. There is no need to make it more complicated then it is.

Jim

---

### Post by moose4204l on 2008-08-14
> **bgerlich said:**
> So you can connect to your router form outside of your lan and you can connect to your http server form inside of your lan, but not form outside?

Sorry for those questions but the answers will give a clear view of the situation.

no, i am inside my network and i can access my website from inside by [http://192.168.0.5](http://192.168.0.5)

i know my public ip address also. 

i cant get to that site from outside when i tell someone to go to it. I tried to port forward http to 8001 so i also told someone to check [http://192.168.0.5:8001](http://192.168.0.5:8001) and that's not working either

---

### Post by moose4204l on 2008-08-14
> **cariboo907 said:**
> You don't need to put public ip address any where in any configuration files on your server, as your server is not directly connected to the internet. Restore your configuration files to their origional state, and do as previous posters have said. Set up a static ip address for your server and set up port forwarding in your router. There is no need to make it more complicated then it is.

Jim


is there a term cmd to get the original state?
from what i can remember, i just put the httpd.conf file back to 
ServerName localhost
ServerName 192.168.0.5

---

### Post by Dylock on 2008-08-14
> **moose4204l said:**
> no, i am inside my network and i can access my website from inside by [http://192.168.0.5](http://192.168.0.5)

i know my public ip address also. 

i cant get to that site from outside when i tell someone to go to it. I tried to port forward http to 8001 so i also told someone to check [http://192.168.0.5:8001](http://192.168.0.5:8001) and that's not working either

Dont use 192.168.0.5, thats the ip address for your server for your network. You want to use the ip address for your router (the ip address that you would see if you went to one of those what is my ip address websites)


do [http://IPFORROUTER:PORT](http://IPFORROUTER:PORT) and you should be able to get to your server.

Quick explanation of whats happening, you use IPFORROUTER which takes you to the router, the router sees that there is a port and says hey i have to check my routing table to see if that should go somewhere, oh it does, lets forward this connection on PORT to internal network ip address 192.168.0.5 which has a program listening on port PORT

---

### Post by OffAxis on 2008-08-14
are you using the virtual host directives at all?

Can you post the relevant part from your httpd.conf or your .conf file from the sites-available folder?

Instead of specifying an IP, you can also get away with using a catch all ( use * instead of 192.168.xx.xx or your wan ip)

---

### Post by moose4204l on 2008-08-14
> **Dylock said:**
> Dont use 192.168.0.5, thats the ip address for your server for your network. You want to use the ip address for your router (the ip address that you would see if you went to one of those what is my ip address websites)

where do  want to use it. do i need to mess with the conf files or what?

---

### Post by Dylock on 2008-08-14
> **moose4204l said:**
> where do  want to use it. do i need to mess with the conf files or what?

No you shouldnt need to change anything. I'm going to make a few assumptions here: (i) you have correctly set up port forwarding to your server (ii) your server is set up correctly to accept connections on the port you specified.

Ok if you are behind a router, there is only one ip address that people on the outside world see, that is the one provided by your ISP. Now the router has multiple computers connected to it, lets say there are three, 192.168.0.1, 192.168.0.2, 192.168.0.3(this is my server). If I tell someone outside my network to connect to my server via 192.168.0.2, it won't make any sense to their computer because that IP address is only defined within my network. Instead I tell them to connect to the IP address that represents my router, lets say its AA.BB.CC.DD. The reason why you set up port forwarding is to redirect traffic that the router gets to a certain computer (or all computers) on your network.

Long story short, if you have set port forwarding correctly, if you tell someone outside your network to connect to [http://ROUTERIPADDRESSTOTHEOURSIDEWORLD:PORT](http://ROUTERIPADDRESSTOTHEOURSIDEWORLD:PORT) you should be good.

EDIT: Something else to keep in mind depending on what kind of router you have, some routers will forward to all computers on the network, which you probably dont want to do, if possible have it only forward to the internal network IP of your server.

EDIT: Added a spiffy mspaint picture since I'm at work :)

---

### Post by moose4204l on 2008-08-14
thats the thing, im not sure if i set it up right. i tried t follow this tutorial... [http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/) ... i just cant get it working

---

### Post by halitech on 2008-08-14
can someone ping the router from outside the LAN with your external IP address?

---

### Post by moose4204l on 2008-08-14
> **halitech said:**
> can someone ping the router from outside the LAN with your external IP address?

how do you ping the server?

---

### Post by cariboo on 2008-08-14
Got to [canyouseeme]("http://www.canyouseeme.org/"). It will show what ip address you are coming from, in the what port box enter port 80 then click the check button you should get a message back, something like this:

```
Success: I can see your service on XX.XX.XX.XX on port (80)
Your ISP is not blocking port 80
```

If you have port 80 open on your router. I substituted x's for my ip address.

Jim

---

### Post by moose4204l on 2008-08-14
> **cariboo907 said:**
> Got to [canyouseeme]("http://www.canyouseeme.org/"). It will show what ip address you are coming from, in the what port box enter port 80 then click the check button you should get a message back, something like this:

```
Success: I can see your service on XX.XX.XX.XX on port (80)
Your ISP is not blocking port 80
```

If you have port 80 open on your router. I substituted x's for my ip address.

Jim

ok this was good. In my port forwarding netgear site, i forward an http on my ifconfig inet addr to port 8001. Still cant get outside access though from another computer


when i put http://<MY PUBLIC IP ADDRESS:8001> in the browser, i get nothing.

---

### Post by doas777 on 2008-08-14
do you have firewalling on on your router? have you checked the logs to see if the packets are being blocked?

one good test is to add a rule to your firewall, that allows but logs packets to that port. then try to connect from outside, and see if you see the logs indicating that those packets were allowed. 

that will tell you if the problem is in the router or the server.

good luck,
franklin

---

### Post by moose4204l on 2008-08-14
i dont know how to check for fire wall. the netgear site does not show an option fo firewalls

---

### Post by doas777 on 2008-08-14
> **moose4204l said:**
> i dont know how to check for fire wall. the netgear site does not show an option fo firewalls

how odd. I used netgear routers for years and always had a packet filter/stateful firewall. what model do you have?

---

### Post by moose4204l on 2008-08-14
RP614v2

---

### Post by doas777 on 2008-08-14
> **moose4204l said:**
> RP614v2

[http://kbserver.netgear.com/products/rp614v2.asp]("http://kbserver.netgear.com/products/rp614v2.asp")


You definitely have a firewall so I'd start looking in your router admin interface for the firewalling/logging features. the problem is likely there, unless you created an exception for incomming connections on your service port.

I gotta run, but good luck and have fun,
franklin

---

### Post by moose4204l on 2008-08-14
i cant find anything.

---

### Post by cariboo on 2008-08-14
What port is apache2 listening to? to find out go to System-->Administration-->Network Tools-->Port Scan, enter localhost in Network Address then click scan, this will do a port scan and will show which ports are open on your computer.

Jim

---

### Post by anewguy on 2008-08-14
I'm running a Netgear WRG614 and having the same problem.  My browser never gets back to my PC (I haven't tried it from another computer yet).  Also, the site mentioned above, never finds port 80 (or port 5900 that I am setting up for tightvnc java) - it just says it times out.  I have port forwarding enabled on the router for port 80 and ports 5900-5905.  I have tried using noip and still cannot access my PC through it either.

I believe we are having the same problem, that is the only reason I have posted here.  I also have not found a log for my router firewall.  I tried the DMZ server option to no avail.  I have to believe there is something in the router configuration that is blocking the ports, but I have no idea what.  Of course it works with localhost, since it never goes out to the "cloud" and back in to my router - everything is just local.

I will be watching this thread, and I'll let you know if I stumble onto something by accident that at least seems to work, as then it might tell one of the experts what to tell us to actually fix it (my stumble-upons usually end up being no-no's but give somebody who actually knows what they are doing a clue so they can tell me what I really should do :) ).

Thanks for letting me add to this thread.

---

### Post by anewguy on 2008-08-14
I found a post in a debian forum that says to actually access the forwarded ports on the router from within the network, you have to use a proxy and go through it to get back to your router.  I don't know squat about any of this, so maybe someone can tell us what to do for Firefox to make this work.

---

### Post by halitech on 2008-08-14
I run a server on my home network and I can hit apache from the machine I'm on by typing localhost or by using my dnydns account and from my laptop by using the internal IP or the dyndns account so not sure what they are talking about

---

### Post by anewguy on 2008-08-14
Yes, we can access from local (within our LAN), but we want to test WAN access (outside of our LAN).  In my instance, I am trying to test remote console.  Yes it works fine within the local network.  But I also want to test from outside my network - e.g., anyone in the nebulous cloud that is the internet.  According to everything I have read, you cannot do this type of testing from within your own LAN, but some have said that if you use a proxy server (I assume thereby your IP is changed to not look like it is within the LAN) you can actually test this.  So, we don't want local testing, but we want local remote testing.

I have a noip account (where that company acts like a go-between) and still cannot access my remote desktop.  Everything times out.

---

### Post by doas777 on 2008-08-15
ok, I believe what you guys are hitting is called "State full packet Inspection" or SPI. basically, it's a firewalling system, whereby all outgoing connections are allowed, and all incomming connections are denied unless they are a response to an internally-initiated connection. 

since you are trying to connect inbound to your nat rule, SPI is likely dropping the connection before it can enter your network.

I've never had any problems finding the firewalling settings in any netgear routers I've worked on (web or telnet), and the specs for the router ([http://kbserver.netgear.com/products/rp614v2.asp](http://kbserver.netgear.com/products/rp614v2.asp)) show it to have a packet filter and SPI capacity. I'm not sure what to tell you, but your problem is likly there.

I hate telling people to read the manual (RTFM), but you will probably have to find out how to access the firewall config for your particluar model. once you find it, feel free to post screen caps and we may be able to help you write the rules you require.

good luck,
Franklin

---

### Post by doas777 on 2008-08-15
> **anewguy said:**
> I found a post in a debian forum that says to actually access the forwarded ports on the router from within the network, you have to use a proxy and go through it to get back to your router.  I don't know squat about any of this, so maybe someone can tell us what to do for Firefox to make this work.

yeah, routing out and then back in through the front door is a bit of a pain. if you have a friend you can call (and ask him/her nicely to try and access your service from their location) you can avoid this headache.

---

### Post by doas777 on 2008-08-15
ok, here is the reference guide for your netgear router.
[http://kbserver.netgear.com/pdf/rp614v2_reference_manual.pdf](http://kbserver.netgear.com/pdf/rp614v2_reference_manual.pdf)

check page 53 for creating a forwarded port. part of that section includes "Adding a Custom Service". a service is in this context a firewall rule. the guide walks you through creating an exception rule ("custom service") that will allow incomming connections to that port.

good luck,
Franklin

---

### Post by anewguy on 2008-08-15
And here in lies the problem - as per 5-3 of the manual you referenced, I already had my ports being forwarded correctly at the router.  That page (or perhaps the next on in reading) stated that LOCAL connections to the router cannot refer to the router by the router's IP address as those connections will fail.  So, flat out, the router does not allow the kind of testing I am attempting, and I believe for the kind of testing the op of this thread was attempting.

So, guess I need to have someone outside of my network attempt it.  If it doesn't work then I'll post again.

---

### Post by doas777 on 2008-08-15
> **anewguy said:**
> And here in lies the problem - as per 5-3 of the manual you referenced, I already had my ports being forwarded correctly at the router.  That page (or perhaps the next on in reading) stated that LOCAL connections to the router cannot refer to the router by the router's IP address as those connections will fail.  So, flat out, the router does not allow the kind of testing I am attempting, and I believe for the kind of testing the op of this thread was attempting.

So, guess I need to have someone outside of my network attempt it.  If it doesn't work then I'll post again.

yeah, sorry, but my post was directed to the thread originator and the specific problem he described. yes you will likely have to call for help from outside, unless you establish a proxy. I'm sorry I didn't make that clear.

you should be able to hit apache from the inside by using the servers lan address/port (not the public address). nothing your router can do could prevent that, since traffic on your network does not pass through it.

I hope that helps,
Franklin

---

### Post by moose4204l on 2008-08-18
I got mine working, thanks for the help. It kind of just started working after I was trying to fix it. Not exactly sure what I did though. It didn't have anything to do with the firewall, unless it need to be refreshed. Thanks for the help though. I will leave this open until the other guy is settled.

---

