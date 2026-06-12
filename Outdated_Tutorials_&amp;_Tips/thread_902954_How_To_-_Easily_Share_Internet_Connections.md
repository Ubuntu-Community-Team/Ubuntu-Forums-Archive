---
title: "How To - Easily Share Internet Connections"
date: 2008-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by ProgenitorVirus on 2008-08-27
Here and around, I've noticed a handful of people looking for answers as to how to simply Share Internet Connections.  

Some people would recommend using Firestarter for Internet Connection Sharing, but then again, a lot of people, like myself, will have to edit a lot of settings for more complex situations.

That's where a Network Bridge comes in handy.  Its essentially the same as ICS, only more flexible, albeit less secure.  You might want to have a firewall remain on your system with it.

Normally, using a series of commands will work when bridge-utils is installed, but they're only for the current session.  We want to make it permanent.

[B]
So onto the task:[/B]



**1.**  Get **bridge-utils** through Synaptic.  This is the software we'll use to create the Network Bridge.

Now, keep in mind to either print this out or not exit your browser, because in this next step we'll stop the Networking Services to change them.

**2.**  Open a terminal, and type

sudo /etc/init.d/networking stop

Keep the terminal open.

**3.**  Now we're going to edit our interfaces file:

gksu gedit /etc/network/interfaces

Replace whatever is there with:


```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1

```

Save the changes.

**4.**  Now we'll restart the Network Services

sudo /etc/init.d/networking start

And there we go.  Your computer is now set up to automatically share its internet connection without dizzying settings for more advanced set-ups!

Have fun, and note longer boot-ups will occur due to creating the network upon boot.

---

### Post by Crafty Kisses on 2008-08-29
Thanks for the tutorial. :)

---

