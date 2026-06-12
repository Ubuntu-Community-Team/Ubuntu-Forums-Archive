---
title: "dyndns?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by rhcm123 on 2008-11-21
How do i use dyndns? I want to be able to access my home server with the service, but every time i try i get my router's control panel. HELP!

---

### Post by scribbles on 2008-11-21
I set it up fairly easily via ddclient. When you go to your dyndns url your router config page shows up?

Some great info can be found [here]("https://help.ubuntu.com/community/DynamicDNS").

---

### Post by rhcm123 on 2008-11-21
yeah, thats exactly what happens.

---

### Post by scribbles on 2008-11-21
Which DynDNS updating daemon are you running?

---

### Post by rhcm123 on 2008-11-21
dyndns.org, if that's what you mean

---

### Post by scribbles on 2008-11-21
Check out that DynamicDNS link I added above. There's multiple daemons to run to update the dyndns servers with your new IP as it changes. You aren't attempting to view your webpage from behind the same router its being hosted on are you? Can you see what you're hosting via [http://localhost/](http://localhost/) ?

---

### Post by rhcm123 on 2008-11-21
> **scribbles said:**
> Check out that DynamicDNS link I added above. There's multiple daemons to run to update the dyndns servers with your new IP as it changes. You aren't attempting to view your webpage from behind the same router its being hosted on are you? Can you see what you're hosting via [http://localhost/](http://localhost/) ?

I only get 1 ip from verizon. How do i set it so can get to my server from the internet.
No, I borrowed a neghibors wifi for this :)

---

### Post by scribbles on 2008-11-21
If it's remote access you're looking for you can follow the documentation [here]("https://help.ubuntu.com/community/SSHHowto") to setup OpenSSH. This will allow you a secure remote login to get to a command line on your server. In order to have one solid domain to login though you will need DynDNS setup properly. Follow [this]("https://help.ubuntu.com/community/DynamicDNS") to get ddclient setup properly. Did you double check the ip's to make sure you weren't just typing in the router ip?

---

### Post by rhcm123 on 2008-11-22
> **scribbles said:**
> If it's remote access you're looking for you can follow the documentation [here]("https://help.ubuntu.com/community/SSHHowto") to setup OpenSSH. This will allow you a secure remote login to get to a command line on your server. In order to have one solid domain to login though you will need DynDNS setup properly. Follow [this]("https://help.ubuntu.com/community/DynamicDNS") to get ddclient setup properly. Did you double check the ip's to make sure you weren't just typing in the router ip?

ok. THANK YOU!!!!!!

---

### Post by lucloubier on 2009-02-02
Hi!

I received an email from DynDNS today telling me my account has no activity during a 30 day period and it will expire in 5 days.

I have ddclient installed on my ubuntu server acting as a router on my home lan.

Here is my ddclient config :

pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
ssl=yes
daemon=86400 

server=members.dyndns.org
login=<my login>
password='my password'
<mydomain>.homelinux.net

My system is using DSL and my IP address is not changing.

How can I force the dyndDNS renewal? I thought it will renew every 24 hours (24x60x60=86400).

Thanks for your help !

---

