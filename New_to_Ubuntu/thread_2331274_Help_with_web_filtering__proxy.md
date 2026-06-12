---
title: "Help with web filtering / proxy"
date: 2016-07-20
forum: New to Ubuntu
---

### Post by tel196 on 2016-07-20
Hi All

I have been using mythbutu as my media centre backend for a while now with no issues at all, its really rock solid but now I am looking at getting the Server to do more, I would really like it to do some proxy and web filtering but I really do not have the time and patience to set it all up from the command line. I have looked at some of the distros like shorewall ipcop etc but I want someting like that with a web interface / gui that I can install on my current server. Ideally it would be transparent to the users as i dont want to set up proxy details on all the laptops / phones / other devices we have.

Thank you for any advice.

---

### Post by TheFu on 2016-07-20
If you want it to be transparent, then it has to be the default route for the network. Usually, that makes it the router. To prevent trivial methods of bypass, you also want the edge router to prevent **all** systems except the proxy from having DNS or internet access.

So ... for most people, the easiest way to accomplish all of this is to replace their edge router with a non-consumer device and run a more capable firewall distro like pfSense/openSense.  There is a learning curve with all of this, but if you have sufficient money, you can purchase an appliance for $800.  I suspect that is more than you'd like to spend - a common trade off is $$$ for time, which also applies here.

I've never used shorewall or ipcop. Prefer BSD for edge firewalls due to the BSD network stack and QoS that actually works.  But that is just me. Know lots of home users stay with Linux-based filewalls and they seem to be very good.
[http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) might be helpful.

BTW, I would never mix router tasks with a desktop or normal server.  It would not be on the same hardware for security reasons - VMs would still be the same hardware. Some people disagree and prefer to place edge routers inside VMs.  For internal routing, fine, but not for the internet filtering/connection.  IMHO.

Welcome to the forums.  Hopefully, someone else will respond with different opinions.

---

### Post by SeijiSensei on 2016-07-20
My usual solution is to put a box behind the firewall router and make it the default gateway for the network.  Then I run [Squid]("http://www.squid-cache.org/") in "[transparent]("http://xmodulo.com/squid-transparent-web-proxy-centos-rhel.html")" mode.  This requires both installing and configuring Squid and adding an iptables rule to redirect outbound HTTP traffic through the proxy.  If you really want to do this, you should expect to get your hands dirty and use the command prompt.  It's possible to manage Squid with something like Webmin, but you would still need to learn how to write "acls" to permit or block specific hosts, domains, URLs, etc.  This takes some time to set up, but not much maintenance after that if your lists of permitted and blocked locations remain relatively constant.

Also remember that filtering HTTPS requests is a whole 'nother ballgame requiring you to create certificates for your client workstations.  I often block HTTPS via iptables rules for that reason.

---

### Post by tel196 on 2016-07-20
Hi, Thank you for your insights maybe I will grab an old low powered machine and chuck in a couple of network cards and give pfsence and some other distros a go. I would have liked to have it all in one but security wise its probably best to keep them separate.
$800 is a bit high for home use. In a few months, time may become less constrained and I can look into all the command line acls and do some real learning in Linux.

---

### Post by tel196 on 2016-07-20
Hi, Thank you for your insights maybe I will grab an old low powered machine and chuck in a couple of network cards and give pfsence and some other distros a go. I would have liked to have it all in one but security wise its probably best to keep them separate.
$800 is a bit high for home use. In a few months, time may become less constrained and I can look into all the command line acls and do some real learning in Linux.

---

### Post by TheFu on 2016-07-21
There are $75 used "desktops" sold at Microcenter and Fry's all the time which can be used for this is you don't mind the power bill (65W-130W of a typical desktop adds up).  A few months ago, got a PCengines APU2 (10W max; 6W normal) for my edge router upgrade - under $150 shipped from Sweden to Atlanta in 3 days.  The trade-off is $$$ or time. Expect the new equipment to last 10 yrs, but *some assembly required* both for the HW and SW setup.  Did some reading about ipcop - looks like an easier way to go than pf. [http://www.ipcop.org/2.0.0/en/admin/html/services-webproxy.html](http://www.ipcop.org/2.0.0/en/admin/html/services-webproxy.html)  BSD is really trying to be friendlier, but they always have security and stability trump everything else.  The $800 is for a point-n-click device; there might be used versions on ebay for less. IDUNNO.

SeijiSensei's ideas are great too. Definitely consider them.

---

