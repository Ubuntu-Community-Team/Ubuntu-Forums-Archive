---
title: "Ubuntu server"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by Halvstrom on 2013-05-01
hi i just installed my ubuntu server and i have a problem, why cant i ping my server from another laptop windows or mac i can ping it when i am in the same network but my friends can't ping me. what must i set in my router to make this work. please i am new to this. help...

---

### Post by TheFu on 2013-05-01
What you need to do is different depending on your ISP and the router.  Also, you can't "ping" through your router without a public IP on the PC.
A better understanding of networking will be needed to get this working.

It is considered a bad idea to allow unlimited ports through to a server, but on many routers this setting is available. It is called a DMZ on home routers, though that is NOT what it really does.  It is extremely dangerous and someone new to networking probably shouldn't use it at all.  Heck, I've been networking for 20+ yrs and there is no way that I'd use DMZ mode at home. **NO WAY.**  A little understanding of network security will be needed so you aren't completely pwond in the first day or month too.

Another option is to setup a VPN server and let your friends connect through that over a completely secure channel.  OpenVPN is probably the best solution. Again, you'll need to understand networking, subnets and routing a little to make it work. 

If you tell us which services you'd like to share with your friends, we can probably provide more details on the appropriate, secure, configuration. If you don't know the services (or ports) yet, then you have some reading to do.

To learn more about networking, there are some great podcasts here: [https://www.grc.com/sn/past/2005.htm](https://www.grc.com/sn/past/2005.htm) and [https://www.grc.com/sn/past/2006.htm](https://www.grc.com/sn/past/2006.htm)
Around episode 25 is where it all starts, but there are some VPN specific episodes earlier.

Understanding internet routing will open an entire world of networking to you.  We all started without knowing anything about networks and slowly learned more and more.  With a little effort, you can too.

---

### Post by cool110 on 2013-05-01
Most NAT routers do not allow incoming pings to be passed through.

---

