---
title: "I'm in California, parents in Ohio..."
date: 2011-10-14
forum: New to Ubuntu
---

### Post by ricardisimo on 2011-10-14
New question: their Ubuntu computer went kaput, and now I'm interested in trying to connect to their Windows machine. Possible? Or not so much?

I tried installing LogMeIn via wine, but no such luck. Any help would be greatly appreciated.

By the way, derrick, how do you call up the ssh once everything is installed? In a terminal?

---

### Post by ricardisimo on 2011-10-14
> **Calash said:**
> You are going to run into a problem if they are behind a router.

ie: if their IP address begins with 192.168 it is a NAT address an will not accept a direct communication without some port forwarding.  There are other addresses as well, but most consumer level routers give you a 192.168 subnet.

Probably the best way to tell is to try and ping the address you got from them.

In a terminal type

ping XXX.XXX.XXX.XXX

xxx being the address.  See if you get a reply.  CTRL-C will stop the pinging.

This makes it sound like, effectively, remote desktop is useless. If in fact most IP addresses are in the 192.168 family, then... ?

---

### Post by sadaruwan12 on 2011-10-14
If this helps when I want to remotely log-in to do some thing I use teamviwer easy and kind of safe for personal use don't recommend it for enterprise grade use.

And the software is available for Ubuntu and fedora most of all it's free.

---

### Post by lisati on 2011-10-14
If you're in different locations, tools like "remote desktop" work better with the public IP address. There are different tools available with different OSes to find out what this is, but one which *should* work with any is by visiting [http://whatismyipaddress.com](http://whatismyipaddress.com)

---

### Post by Rubykuby on 2011-10-14
You should install teamviewer. It's a pretty nice remote desktop program that just works and is compatible with all OSs. The downside may be explaining your parents how to install it.

Worth a try, I'd say.

---

### Post by sadaruwan12 on 2011-10-14
> The downside may be explaining your parents how to install it.


Well it's no issue installation is pretty straight forward Download the .deb package double click package and insert the root password and let the APT do it's magic.

After that log in remotely using the temporary password that get provided by the TeamViwer servers after the first log in configure a permanent password so you can log in after word with out your parents intervention.

---

### Post by ricardisimo on 2011-10-17
TeamViewer did the trick. Thank you so much!

---

