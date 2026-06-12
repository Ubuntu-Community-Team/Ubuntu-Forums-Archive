---
title: "Change IP Address for Apache?"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by justinram22 on 2008-10-10
Hello, Im wondering how to go about this... Im behind a router, and im running apache, and im able to veiw my files that i put in /~/www/ through my other computers on my same network (i.e. 192.168.1.xxx:80) but my ip address is the same (it's 12.218.xx.xxx) on all my computers, and im wondering how like, lets say my friends, are supposed to veiw them? any help would be greatly appreciated

---

### Post by Ohs0Ahxi on 2008-10-10
You will need to forward port 80 on your router to the IP address of the machine running apache.

So in my case i would log onto my router and find the port forwarding section, and i fill in the external port number (80) internal number (80) and the internal address (192.168.2.xxx < the apache machine)

If you need help figuring out port forwarding take a look here [PortForward.com](http://www.portforward.com/guides.htm) or reply in here.

---

### Post by drewcoon on 2008-10-10
Your router should assign a local IP address for every computer on your network, try in terminal:

```
ifconfig | grep "inet addr"
```

This should show your local IP as something like inet addr:192.168.1.xxx

From here, you have to set up your router to forward traffic on port 80 (default port for web clients to use), to the local IP of the computer which is running apache.

Setting up port forwarding on routers differs depending on what make and model of router you have, so if you need help, you should google for port fowarding with your router model.

Hope I've helped :)

---

### Post by dhtseany on 2008-10-10
Hey just a suggestion: Don't post your public IP address on a public forum such as this. Some people with ill intentions could take that and try to "hack" into your stuff. I'd edit your post and remove it.

Peace
Sean

---

### Post by dhtseany on 2008-10-10
One more thing: If you want to make it easier to give your address to your friends, try out some of the free [dynamic DNS]("http://en.wikipedia.org/wiki/Dynamic_DNS") services such as:

[http://dyndns.org]("http://dyndns.org") or [http://ddns.nu]("http://ddns.nu")

Those are my two favorites.

Peace
Sean

---

### Post by bodhi.zazen on 2008-10-10
> **dhtseany said:**
> Hey just a suggestion: Don't post your public IP address on a public forum such as this. Some people with ill intentions could take that and try to "hack" into your stuff. I'd edit your post and remove it.

Peace
Sean

IMO this is not really a big security risk. At one time perhaps this was true, but security through obscurity is no security at all.

If you run a public server, be sure you understand how to secure it ;)

---

### Post by justinram22 on 2008-10-10
Ok, so now im able to view my site with my IP address.. but now im trying to register it with my domain name, (it's from [www.godaddy.com](www.godaddy.com)) and it asks for 2 nameservers? what am i supposed to put here? why can't they just make it simple and put "put IP address here?" lol anyway, the only way i can think to get it to work is to make a site like "ramsey22.biz.vi" and have that forward to my ip address (as for they made it simple) from [http://freedomain.biz.vi/](http://freedomain.biz.vi/) and then have godaddy forward my site to the "ramsey22.biz.vi" one, but there must be a simpler way, and it i were to ever to business, that wouldn't look very professional.... Thanks for any help

---

### Post by bodhi.zazen on 2008-10-10
> **justinram22 said:**
> Ok, so now im able to view my site with my IP address.. but now im trying to register it with my domain name, (it's from [www.godaddy.com]("http://www.godaddy.com")) and it asks for 2 nameservers? what am i supposed to put here? why can't they just make it simple and put "put IP address here?" lol anyway, the only way i can think to get it to work is to make a site like "ramsey22.biz.vi" and have that forward to my ip address (as for they made it simple) from [http://freedomain.biz.vi/](http://freedomain.biz.vi/) and then have godaddy forward my site to the "ramsey22.biz.vi" one, but there must be a simpler way, and it i were to ever to business, that wouldn't look very professional.... Thanks for any help

Once you have registered with GoDaddy I suggest you call their tech support. They will walk you through the setup.

Once you make the changes it can take up to 24 hours for your new domain to propagate through the system.

---

### Post by dhtseany on 2008-10-11
> **bodhi.zazen said:**
> IMO this is not really a big security risk. At one time perhaps this was true, but security through obscurity is no security at all.

If you run a public server, be sure you understand how to secure it ;)

Agreed, but for the beginner home user who is playing around with port forwarding and firewall exceptions for the first time, annoyminity will help at least keep them from people who want to see if they can get in. I'm not sure that was the best wording choice but at least I tried :)

Peace
Sean

---

### Post by bodhi.zazen on 2008-10-11
> **dhtseany said:**
> Agreed, but for the beginner home user who is playing around with port forwarding and firewall exceptions for the first time, annoyminity will help at least keep them from people who want to see if they can get in. I'm not sure that was the best wording choice but at least I tried :)

Peace
Sean

I know, I understand. But these days that is just not much protection, there are just too many "script kiddies" as they are called, automated methods of finding open ports.

---

