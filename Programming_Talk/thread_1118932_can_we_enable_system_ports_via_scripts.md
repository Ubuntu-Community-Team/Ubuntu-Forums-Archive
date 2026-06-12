---
title: "can we enable system ports via scripts?"
date: 2009-04-07
forum: Programming Talk
---

### Post by abhilashm86 on 2009-04-07
when using telnet or ssh, to confirm routines of port numbers 22 and 23, i don't know how to check those ports are active.
So how should we actually do that? via scripts or any commands?

---

### Post by ajgreeny on 2009-04-07
Are you running a firewall which is changed in any way from the default setup which you get at install?  If everything is as it was at installation you don't need to do anything;  all ports will be available to you when you ask them for some action.  If you have a custom firewall setup running, you may need to ensure that those ports are available, but I'm afraid someone else will have to tell you how, as my machine has no firewall applications running except the default setup of iptables, and I haven't a clue how you can do it.

---

### Post by abhilashm86 on 2009-04-07
> **ajgreeny said:**
> Are you running a firewall which is changed in any way from the default setup which you get at install?  If everything is as it was at installation you don't need to do anything;  all ports will be available to you when you ask them for some action.  If you have a custom firewall setup running, you may need to ensure that those ports are available, but I'm afraid someone else will have to tell you how, as my machine has no firewall applications running except the default setup of iptables, and I haven't a clue how you can do it.

oh ok, even i'm newbie to networks, i don't have a custom firewall, but i've configured some to use bit torrent file downloads via some ports..........
when i use telnet, OS in turn just will try connecting.........
but it just hangs, so i thought we need to configure these ports to make available, maybe if my guess is correct:)

---

### Post by ajgreeny on 2009-04-07
You may need to enable port forwarding for the torrent application to work.  How you do that will depend on the application you use.  I like ktorrent, even though I use gnome, and in the setup for that there is a button to enable it.  Have a look in whatever you use to see if it's needed and if so, enable it.

---

