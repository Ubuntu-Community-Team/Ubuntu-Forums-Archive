---
title: "Comcast Account Setup Help Needed (Intrepid)"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by jango102 on 2008-11-20
When I first installed Ubuntu (Hardy) on my desktop computer, it worked just fine with my regular wired Internet connection, provided by Comcast. Some days back, Comcast suddenly shut off our connection on account of our missing a payment or something of the sort. The issue was sorted out, and the connection was restored. All of the other computers in the house, all running Windows XP (with the exception of my PSP), can now connect just fine, but whenever I try to browse the web on my desktop, it displays a Comcast.net page that tells me that my operating system is not supported by their Account Setup manager. I have absolutely no idea what to do, even after searching around for solutions to my problem. Any ideas?

---

### Post by prshah on 2008-11-20
> **jango102 said:**
> 
All of the other computers in the house, all running Windows XP, can now connect just fine, 

Let's take a look at the configuration you're using on XP; Click Start-Run, give the command ```
cmd
``` and press enter. In the new (black) window that opens up, give the command ```
ipconfig /all
``` 

Then, from your Ubuntu computer, open a terminal (Applications-Accessories-Terminal) and post back the results of ```
ifconfig
iwconfig
```

Are you using wireless or wired? 

Post back the results here for detailed setup steps.

---

### Post by gpsmikey on 2008-11-20
Are you connecting your machines to Comcast through a router or is each machine connecting directly to the cable modem (or possibly with a hub/switch but no router) ?  At least in our area, Comcast has nothing installed on any of my machines (some XP and some Linux).  If you are going through a router, then start by comparing the DNS addresses the working machines show vs the confused one.  The key question here that makes a big difference is "is there a router between your machines and the Comcast cable modem" ? :)

mikey

---

### Post by Kellemora on 2008-11-21
Hi Jango

I'm on Comcast too and I get that same display page every once in awhile myself.

This was something new to me too as I had never gotten it before about 3 weeks ago ever.

My wife has an XP machine, and I have one I use for accounting and front office.  If both XP machines are turned off is when I would start getting that message and couldn't connect.  Took awhile to figure out what was going on here too.

How I fixed it was to just unplug and plug the router back up again while the XP machines were turned off.  Then it came up and worked fine!  I didnt' make any changes to anything myself other than what the router does when it reboots itself.

I've never tried connecting anything without a Router and Firewall.  So if you don't have a router, I don't know what to tell you, other than routers are cheap these days.

TTUL
Gary

---

