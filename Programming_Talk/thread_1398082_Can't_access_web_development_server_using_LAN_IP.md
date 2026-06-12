---
title: "Can't access web development server using LAN IP"
date: 2010-02-04
forum: Programming Talk
---

### Post by prvteprts on 2010-02-04
I am trying out Google App Engine on Eclipse 3.5. I am able to access the web server and application through localhost as well 127.0.0.1 on the same machine. But I can't access it through the 192.168.2.x either on the same machine or another machine in the local network. I also tried running an app from the command line (without Eclipse) and I got the same result.

I have used GlassFish on Netbeans before, and I recall I didn't have much trouble accessing it then. Any suggestions? Thanks.

---

### Post by mikejonesey on 2010-02-04
firewall? look in system->admin-> for a firwall option otherwise google iptables, also i'd reccomend installing webmin to manage all your network/host settings (makes life easyer).

hope this helps

---

### Post by fireandlight27 on 2012-01-14
I imagine after 2 years you've probably worked around this problem, but for anyone else who found this as the first relevant search result when attempting to solve this problem, I found this:

[http://www.cuberick.com/2008/11/access-google-app-engine-development.html](http://www.cuberick.com/2008/11/access-google-app-engine-development.html)

Which suggests using the proxy pen:

sudo apt-get install pen
pen 8079 localhost:8888

This will cause any traffic coming in through 192.168.1.x:8079 to be forwarded to the local GAE server on 8888.

---

