---
title: "i dont need antivirus do i need a firewall."
date: 2009-09-07
forum: Recurring Discussions
---

### Post by wlraider70 on 2009-09-07
since everything i see tells me that i don't really need an anti-virus.
Do I need a firewall. If I do is there a software firewall that will work?

---

### Post by amauk on 2009-09-07
Linux has a firefall built-in,
it's called iptables

Linux, by default, runs with all ports closed.
Unless you're running server software, you do not need to do anything.

If you **are** running server software (SSH, HTTP, FTP, etc.) then it's a good idea to restrict open ports to known external IP addresses

---

### Post by MC707 on 2009-09-07
iptables is a very powerful tool. But you know which one is more secure? Common sense :P and good+secure passwords. :) linux is a pretty secure OS in itself, too.

---

### Post by running_rabbit07 on 2009-09-07
Ubuntu has a simple firewall program called Firestarter, which can be installed via Synaptic Package Manager or using the following code. Jus copy and paste it into terminal.  ```
sudo apt-get install firestarter
```

---

### Post by mikewhatever on 2009-09-07
It's worth mentioning that Firestarter is just a graphic interface for managing iptables, same as gufw. Both shouldn't be needed for a general home user.

---

### Post by running_rabbit07 on 2009-09-07
> **mikewhatever said:**
> It's worth mentioning that Firestarter is just a graphic interface for managing iptables, same as gufw.

I learn something new every day. That is good to know.

---

### Post by Sgt-Slyde on 2009-09-08
I personally install Firestarter on all my home-use boxes as the GUI is easier to talk people through when they need to make changes.  Most of the changes I've had to do is opening ports to allow LAN file sharing among multiple computers on the same home network.  As amauk wrote, Linux runs with ports closed - the GUI Firestarter makes it easier/safer to selectively open the ports you need.

---

### Post by lisati on 2009-09-08
Opinions vary on the need for anti-virus. If you're likely to use your Ubuntu box to interact with Windows boxes, it won't hurt to have some means of avoiding passing on viruses on to the Windows boxes in place.

---

### Post by sasho_zl on 2009-09-08
Firestarter is pretty much out of date. It s not supported for years. 
You can install gufw from synaptic. Even if you don't run any listening services it wont hurt to turn your firewall on because you allready have it in your system. It has one advantage - if configured the right way it will prevent people and mallware scripts from pinging your PC and it will significally increase the time for scanning your ports.
And one more thing - the linux kernel firewall is NETFILTER. Iptables is just another tool for configuring it.

---

### Post by HermanAB on 2009-09-08
Linux pretty much *IS* a firewall.  Most commercial firewalls run Linux.  That is why you don't really need to add a firewall in front of a Linux machine.

Firewalls are really mostly a Windows phenomenon, since on a Windows system, you never know which ports are listening to what, so an external band-aid is required in a (ultimately futile) effort to make it safe.

---

### Post by sasho_zl on 2009-09-08
> **HermanAB said:**
> Linux pretty much *IS* a firewall.  Most commercial firewalls run Linux.  That is why you don't really need to add a firewall in front of a Linux machine.

Firewalls are really mostly a Windows phenomenon, since on a Windows system, you never know which ports are listening to what, so an external band-aid is required in a (ultimately futile) effort to make it safe.

I couldn't agree more. Windows is a system that never should have been plugged to a network. It was never meant for that and that is why security holes from the first versions are still exploitable today.  Simply:
[CENTER]**Windows + Internet = BAD **

[/CENTER]
On the other side - GNU/Linux and Unix - they were born in the network.

Proof of concept: [http://lists.grok.org.uk/pipermail/full-disclosure/2009-September/070568.html     ]("http://lists.grok.org.uk/pipermail/full-disclosure/2009-September/070568.html")

:lolflag:

---

### Post by dk06 on 2009-09-08
You already have a good software firewall (iptables)
-&-
I highly recommend a separate hardware firewall (router)
--Cisco/Linksys and SMC make quality routers...Netgear is good too.

Defense in depth is good practice and many hardware firewalls do use a linux kernel, I just prefer a separate box to do the majority of my filtering.
(kinda like a wall around the castle, yeah...the gate works but why not spend the $35 for the wall.)

---

### Post by wlraider70 on 2009-09-08
on an a side note, i saw that in fire starter you can bridge network connections, does that work?

---

### Post by phillw on 2009-09-08
> **sasho_zl said:**
> Firestarter is pretty much out of date. It s not supported for years. 
You can install gufw from synaptic. Even if you don't run any listening services it wont hurt to turn your firewall on because you allready have it in your system. It has one advantage - if configured the right way it will prevent people and mallware scripts from pinging your PC and it will significally increase the time for scanning your ports.
And one more thing - the linux kernel firewall is NETFILTER. Iptables is just another tool for configuring it.

You can't 'turn a firewall on' in linux - linux **IS  a **firewall - users only turn bits of it **OFF**. !!!

FireStarter is not so much 'out of date' as got to the point where you cannot improve on perfection. That being a nice easy way to configure up IP tables, without having to manually edit them.

**ALL** 'firewalls' configure up IP tables - firestarter does it very well, if you are running a full blown server, then you can look at Shorewall.
Then again, if you want to go down that route you're going to need this ...

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

IMHO, firestarter will do for you linking up computers at home - as noted earlier, most routers have decent firewalls, so you can rest in peace.

If you'd like to delve into how NETFILTERS uses IPtables to 'talk' to it, there documentation site is here.

[http://www.netfilter.org/documentation/index.html](http://www.netfilter.org/documentation/index.html)

Phill.

---

