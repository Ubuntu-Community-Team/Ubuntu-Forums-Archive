---
title: "Setting up server for offline development"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by ZarathustraDK on 2008-10-26
Hey, I guess this falls in the newbie-category since I'm not that familiar with the server-side of things.

Long story short: I want to secure my apache-server so only myself can browse localhost for website-testing-purposes. I've tried doing what it says here : [https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache](https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache) but when I change
```
listen 80
```
to
```
listen 127.0.0.1:80
```
in ports.conf going to local host just gives me a 
> "Failed to Connect

      
Firefox can't establish a connection to the server at localhost.


Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

Any ideas?

---

### Post by Dedoimedo on 2008-10-26
Hello,

Use the listen directive for ports. If you wish different IPs to listen to different ports, then use virtualhost containers.

Furthermore, without a DNS in place, no one will be able to reach you without specifying the exact IP of your machine. Is this IP internal or external? If your server uses an internal address, then you're ok.

Still, you can simply limit the traffic to your machine using the firewall. Do not allow incoming traffic on the external interface on port 80 and you're set.

If you need detailed help, please tell, I'll try to help.

P.S. Try the guide in my sig.

Dedoimedo

---

### Post by ZarathustraDK on 2008-10-26
I haven't configured any dns-server stuff.

Furthermore I'm on a dhcp-connection through an external router. I don't know if that tells you anything about whether the IP-adress is external or internal.

I'm a bit shot on the whole server-lingo, but I can access localhost if I just leave the ports.conf on "listen 80", it's when I change it to "listen 127.0.0.1:80" that it doesn't work as intended.

Hope it helps. I don't need my server to do anything else than let me test webpages, no ip-serving, no being visible to other computers on the network.

---

### Post by Dedoimedo on 2008-10-26
Hello,

If you have a router, then you're probably all set. If no port is forwarded on the router, then all your traffic will be internal only.

Use listen directive without IP address, only ports.

And use firewall to limit traffic to your local machine only.

Dedoimedo

---

### Post by ZarathustraDK on 2008-10-26
Ok, thanks for the info :)

---

