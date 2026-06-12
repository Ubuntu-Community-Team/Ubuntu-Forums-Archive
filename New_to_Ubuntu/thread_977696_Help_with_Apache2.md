---
title: "Help with Apache2"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by geomur on 2008-11-10
Although new to Ubuntu, I need to host a small website and am trying to set it up using Apache2.  The set-up/configuration instructions I've found on the web (esp. Apache's website) seem pretty opaque (or perhaps I'm just being dim) but I'd be very grateful if soemone could advise me on configuration/getting it working through DynDNS (or point me to an exisiting beginners guide.)

Many thanks, everyone.

Geoff

:confused:

---

### Post by ggaaron on 2008-11-10
I don't think that apache configuration has anything to do with dyndns configuration. For apache - just install it, it will have it's standard configuration, and will just work. You should put your website in /var/www/ directory and try localhost in your browser.

---

### Post by jimv on 2008-11-10
Install apache2 on your machine.  Open Firefox and type

[http://localhost](http://localhost)

You should get a "It works!" message.  If you get that, then your webserver is working.  Then next step is to go onto your router and forward port 80 to your webserver so people on the internet can get to it.

Then you need to setup a domain name to point at your IP address.  That's what the dynamic dns is for.  Here's the great community documentation for setting that up.

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by geomur on 2008-11-11
Many thanks Folks.  That's got me going, all your responses were much appreciated!

Best wishes

Geoff

:)

---

