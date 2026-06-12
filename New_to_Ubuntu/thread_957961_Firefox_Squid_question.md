---
title: "Firefox Squid question"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by coldcoffee on 2008-10-24
I have squid installed on a computer and have it so it will block certain sites. Is there a way to disable someone from being able to go in to the preferences menu on firefox on user accounts and changing the proxy settings if they happen to figure out that is all they need to do to bypass filter settings?

Thanks in advance for any help.

---

### Post by Dr Small on 2008-10-24
This tutorial should help get you started:
[http://www.linux.com/articles/113733](http://www.linux.com/articles/113733)

---

### Post by coldcoffee on 2008-10-24
I will check it out. I hope it answers my question. Regardless, thank you.

Edit be here:

I followed the directions on the site. I am sure they work, but for me I ended up having no Internet access at all after I did it all. I didn't really care for the fact DansGuardian installed Clam anti-virus either. I will eventually try it again though and I do appreciate the link.

I did however find that I needed to set a line in Squid to **http_port 127.0.0.1:3128**. This is to allow only localhost to use the Squid proxy. It was not commented out and it was simply **http_port :3128**. I am assuming that might possibly allow others to use my computer for proxy services which wouldn't be good at all. That is if they were smart enough to hack in and use it.

Don't know if that is what that means, but if so I definitely learned something very valuable.

I have it to where Squid is blocking the sites on it's own again. And the user I am trying to block from said sites I don't think is geeky enough to go in and disable it through the preferences option in Firefox. But I would like to be able to eventually figure out how to keep this from happening just to be safe.

Thanks

---

### Post by Dr Small on 2008-10-24
> **coldcoffee said:**
> I will check it out. I hope it answers my question. Regardless, thank you.
The part down at the bottom about iptables should apply to you, and basically make a transparent proxy on your computer. No need to connect to it in Firefox, as all connections will pass through the proxy server.

---

### Post by coldcoffee on 2008-10-24
I am mainly posting this to hopefully make sure it will be seen again. I entered these commands through the terminal as it said.

iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner squid -j ACCEPT

iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner squid -j ACCEPT

iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8080

iptables -t nat -A OUTPUT -p tcp --dport 3128 -j REDIRECT --to-ports 8080

The reason I post this is I truly don't understand what they mean. I believe they are redirecting certain traffic to port 80 and 3128 to 8080 for the filtering services. I uninstalled DansGuardian and Clam AV since it didn't work for me at the moment. I was already previously using Firestarter, even though ports are closed, but I prefer to stealth them and haven't obtained the geekiness to do it through IPtables on my own. Everything seems to be fine, but will these settings affect anything now with software removed? Will these settings stay permanent till I manually remove them, is it something that may affect me later in some crazy way?

Thanks

---

