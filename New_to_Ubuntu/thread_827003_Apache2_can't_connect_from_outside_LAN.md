---
title: "Apache2 can't connect from outside LAN"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Nitewalker on 2008-06-12
I have installed Apache2 and seems to work from my LAN alright as I can see pages on my web browser, but I can't access it from outside my home network.  I have an account with dyndns and am using an address of xxxx.homeip.net, and my network address of where the Apace2 is installed is 192.168.0.xxx.  I have a DSL modem and it is hooked to my DLink-624 wireless router.  I have been reading all the pages I can but can't find out what I am not doing right to be able to see it from outside my LAN.:confused:

---

### Post by Titan8990 on 2008-06-12
Are you forwarding incomming HTML requests on your router to your web server?

---

### Post by _sphinx_ on 2008-06-12
The problem may be due to the ISP blocking all inbound connections.

---

### Post by hyper_ch on 2008-06-12
(1) Assign your box a static IP in the lan

(2) forward port 80 from your router to your box

---

### Post by Cypher on 2008-06-12
Do everything **hyper_ch** said, but instead of using the standard port 80, use something random only you know. With the standard port 80, you'll find that your machine is going to start gettint web traffic for no reason. Especially if you end up using a URL with DynDNS that was previously assigned..

---

### Post by Nitewalker on 2008-06-12
I have set up my router to allow port 80, 22, 5900 to the machine IP of 192.168.0.xxx, and set up "Firestarter" to allow traffic from laptop on network.  Do I need to place a policy in firewall program to allow all to enter port 80:confused:  If I do what is it that I put in the policy field for who to allow.

---

### Post by Titan8990 on 2008-06-12
Personally, I disable firewalls for this kind of troubleshooting. This rules out the firewall being the problem.

---

### Post by Nitewalker on 2008-06-13
I have checked both my port 80 and 22 and both are open through the firewall.  I still can't access my sight from outside my own LAN?  Have read all the help files I can find but still am not sure if I am missing something in one of the conf files.:(

---

### Post by OffAxis on 2008-06-13
Have you tried reaching your WAN IP directly?
You can use whatismyip.com to get it and then just try typing it in as the url.


did you try disabling the router's firewall like Titan8890 suggested?
You could set your machine's IP to DMZ on the router and that would do it.
It could be a problem with the router. Can you get any traffic forwarded through it?

You could also try removing the router and connecting your computer straight into your internet connection; that would do it, too.
Then you could try getting your WAN IP address or your dydns name without the router's firewall possibly messing you up.

---

### Post by Nitewalker on 2008-06-13
Did what you suggested and had someone try and reach it from the WAN at work and they were able to do it by putting the IP address and it came up alright, but if they try and put in the URL [http://xxxx.homeip.net](http://xxxx.homeip.net) it errors out and says can't display web page?  I am using dyndns and ddclient, and am wondering if I have messed something up in the conf files:confused:

---

### Post by spiderbatdad on 2008-06-13
You original post is slightly confusing. What IP address have you registered with DYNDNS? The post suggests you have registered you local IP address. Of course that would not work.

---

### Post by feign2 on 2008-06-13
> **Nitewalker said:**
> Did what you suggested and had someone try and reach it from the WAN at work and they were able to do it by putting the IP address and it came up alright, but if they try and put in the URL [http://xxxx.homeip.net](http://xxxx.homeip.net) it errors out and says can't display web page?  I am using dyndns and ddclient, and am wondering if I have messed something up in the conf files:confused:

Just to expand on spiderbatdad, your dyndns must point your xxxx.homeip.net to your WAN ip, then your wireless router must port forward your incoming port 80 (and port 443 if you also wanted https) traffic to the LAN ip (192.168.0.xxx).

To check what xxxx.homeip.net points to, open a console and enter the command:
$ host xxxx.homeip.net

For DLink-624 (I don't have one, looked up on the internet), port forwarding is done through the router's Advance->Virtual Server page.

[Edit] Missed the ddclient part. This is probably your problem.
You should not need to use ddclient in this case (since it only knows the LAN ip if run inside a LAN pc). Your wireless router already has its own ddns handshake mechanism. E.g.

[http://www.no-ip.com/support/guides/routers/using_the_dlink_di614_internal_ddns_client.html](http://www.no-ip.com/support/guides/routers/using_the_dlink_di614_internal_ddns_client.html)

[Edit 2] Looks like dyndns don't like router ddns
[http://www.dyndns.com/support/kb/cat_routers.html](http://www.dyndns.com/support/kb/cat_routers.html)
So you just need to get your ddclient setting right.

---

### Post by Nitewalker on 2008-06-14
I have my dlink rounter enabled for dyndns and also have in the ddclient conf file a entry "use=dlink-624  fw:=192.168.0.1"  Still can not connect to [http://xxxx.homeip.net](http://xxxx.homeip.net) from the WAN, but they can connect it the put in my IP address xx.xxx.x.xxx. 

Does it matter if I have got my router ddns enabled and also using ddclient? 

When I did "host xxxx.homeip.net I get the following:  xxxx.homeip.net has address 72.16x.xx.2xx, which is the address that DYNDNS shows for my site, 

IP Address:72.16x.xx.2xx
Use auto detected IP address 72.16x.2.xx6.
TTL value is 60 seconds. Edit TTL.

I am not sure which way to go from all the reading that I have been doing, sure do appreciate your all helping get me on the right track:)

---

### Post by spiderbatdad on 2008-06-14
If entering your public ip is working. I tend to think the problem is with the DYNDNS site configuration.

One other thing could be, have you set the ServerName setting in httpd.conf and virtual host directory?

ServerName xxxx.homeip.net

---

### Post by Nitewalker on 2008-06-14
can't seem to locate the "httpd.conf" file, and not sure where the virtual host directory is either...:confused:

---

### Post by spiderbatdad on 2008-06-14
In the repo version from synaptic:

/etc/apache2/

You can also use: Places>>Search For Files.

or from the terminal:```
sudo updatedb
locate apache2
```

updatedb= update database

---

### Post by Nitewalker on 2008-06-14
I want to thank you all for trying to help me, but I think for now it is back to the "books" for me and to try and reread all the stuff and see if I can find out what is going on, because today the access IP is different that yesterday and if you don't use the new one you can't get in, and when I check my host page at dyndns it shows today's IP.  So to free your minds up for being able to help others I will go back to the "books", but wanted to thank you all for your assistance.:popcorn:

---

### Post by halitech on 2008-06-14
try having someone ping the IP and the hostname you are using, see if the hostname translates to the proper IP, might be a case of something on the DNS servers going haywire and not translating properly.

---

