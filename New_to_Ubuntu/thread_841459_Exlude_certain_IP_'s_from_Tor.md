---
title: "Exlude certain IP 's from Tor"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by fychan on 2008-06-26
I have Tor, Privoxy and Squid running on my box without any (major) issues.

However, the problem I now have is that I have several website administration tools (phpMyAdmin, Nagios etc) which run on an Apache server - secured using an "Allow from X.X.X.X" definition.

Using Tor I cannot get access to the admin tools any more - because it is "disguising" my IP address.

I cannot find any config settings to tell Tor to avoid using its network for given IP addresses - is there any setting like:

[FONT="Courier New"]exclude_ip 127.0.0.1, 192.168.1.0/255.255.255.0[/FONT]

Am I missing something - or is it not possible?

[edit] I should've mentioned that this is running as a home server for a small network (hence the squid for "protecting the kiddies") - so any PC on the 192.168.1.X subnet requesting any site on the X.mydomain.com domain (or local subnet) shouldn't go via Tor, as all those sites are sat on my local server [/edit]

---

### Post by forger on 2008-06-26
you could use a firewall, or learn iptables (which I haven't still mastered, so I can't be much of a help)

---

### Post by fychan on 2008-06-26
Sorry, but I'm missing how I can tell any firewall that I want any requests going out through the Tor network with a final destination of X to redirect internally...  I'm feeling very slow today :(

---

### Post by aashay on 2008-06-26
Pardon my complete ignorance about web administration, but do you use firefox to access the tools remotely?

---

### Post by fychan on 2008-06-26
> **aashay said:**
> Pardon my complete ignorance about web administration, but do you use firefox to access the tools remotely?

Yes - that's exactly how it works - they're a kind of web GUI.  There's some sample [demo's for phpMyAdmin]("http://pma.cihar.com/").

I also use the [Nagios front end]("http://www.nagios.org/about/screenshots.php"), as well as [Fruity]("http://fruity.sourceforge.net/") to easily configure the Nagios config files, my email spam filter and some of my own custom written admin tools to edit the whitelist for the kids web filter...

I obviously don't want anyone else playing with these - so I secured access to them using Apache.  Rather than use a username / password which could be cracked I thought I'd lock it down to only be available via my internal network.  When I want to access the tools from outside my network, I SSH onto my server and port forward the proxy port - then set Firefox to use a proxy of "localhost:3128".  That way the requests from the external machine appear to originate from inside my network, and Apache lets them through.

With Tor - that no longer happens.  They appear to come from Sweden, or Turkey, or the US, or even just down the road... But never 192.168.1.X - even when made from the box itself :(

---

### Post by aashay on 2008-06-26
Well, frankly, I didn't understand most of what you said, but thats just me. What I would suggest is to use the Foxyproxy firefox addon unless you are already using it. It'll allow you to bypass tor and use a direct connection or even use some other proxy for certain ips. Which is what you wanted to do as I understand it

---

### Post by fychan on 2008-06-26
> **aashay said:**
> Well, frankly, I didn't understand most of what you said, but thats just me.
Sorry :oops:  It boils down to GUI front-ends that are available on the web - with the web server blocking access to anyone outside my subnet.  Hope that's clearer :D

> **aashay said:**
> What I would suggest is to use foxyproxy unless you are already using it.
I am already using it - thank you.  Unfortunately, it doesn't work in this case for Reasons™ (if you thought that lot was complicated you certainly don't want to know about this lot).

I think I could get around the problem by editing the hosts file on each PC and then setting up foxyproxy to tie in with those - however I was hoping there would be a setting in Tor that would mean I wouldn't need to keep changing settings on each PC everytime I modify a subdomain / new domain...

---

### Post by aashay on 2008-06-26
Maybe Privoxy is what you need to look into not tor. After all its privoxy which forwards the requests to tor. Anyway, I was looking around and saw this: [http://www.privoxy.org/user-manual/config.html#FORWARDING](http://www.privoxy.org/user-manual/config.html#FORWARDING)
Hope it helps.

---

