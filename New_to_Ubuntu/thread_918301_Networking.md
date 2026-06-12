---
title: "Networking"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by OttoDestruct on 2008-09-12
I'm trying to work out a weird networking issue. The university I'm at doesn't allow routers, but I still want my wireless devices to have internet access. I'm trying to configure things so it looks like this:

ethernet -> computer -> router -> wireless devices

I have two ethernet ports on my computer, one receiving the internet (eth1), and I want the other to go to the router (eth0) so I can share my internet.

How should I be setting things up in ubuntu and on my router? (wrt54g running Tomato)

---

### Post by Rolcol on 2008-09-12
This seems like what you're talking about: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)  You can try Firestarter which is a GUI for iptables.  You can use the wizard to set up connection sharing.

---

### Post by komoto on 2008-09-12
Sounds to me like you want to make your computer a NAT device (which can be done with the firestarter application), and you want your router to behave like a switch.  I imagine you have to look for an option on your router to make it an AP (access point).

What you're trying to do is conceptually quite simple, but I normally struggle with that task, even though I've used GNU/Linux systems for a long time.  Normally I end up playing around with iptables and even the kernel.

These days I tend to just use a dedicated firewall computer with a dedicated operating system designed for just that purpose.  [pfSense]("http://pfsense.org") is good for that purpose.  It requires knowledge of networking, but if you know that stuff then it presents all the options in a very clear and understandable web-based interface.

-Kom

---

### Post by OttoDestruct on 2008-09-12
Ok I've got it so my devices can connect to the router, but the connection is still not being shared. Any ideas to check for why?

Should my ethernet from my computer be connected to one of the switch ports to the router, or to the internet port.

---

### Post by Rolcol on 2008-09-12
> **OttoDestruct said:**
> Ok I've got it so my devices can connect to the router, but the connection is still not being shared. Any ideas to check for why?

Should my ethernet from my computer be connected to one of the switch ports to the router, or to the internet port.

The ethernet cable coming from the computer going to the router goes in the Internet port.

---

