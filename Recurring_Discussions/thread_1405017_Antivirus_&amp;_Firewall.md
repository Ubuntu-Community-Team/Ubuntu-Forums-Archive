---
title: "Antivirus &amp; Firewall"
date: 2010-02-12
forum: Recurring Discussions
---

### Post by eranga1988 on 2010-02-12
Is  it necessary to use a antivirus and a firewall for ubuntu???Then what packages do you recommend to use???:)

---

### Post by OrangeCrate on 2010-02-12
An often asked question around here. This should help you to understand the differences between Windows and Linux regarding security issues:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by mcduck on 2010-02-12
No, in most cases you don't need either one. :)

There are no Linux viruses runnign in the wild, actually the few that even exist are mostly proof-of-concepts that never spreaded in the wild. There are some antivirus apps for Linux but those only scan for Windows viruses and are intended to be sued on mail servers etc. to protect Windows machines.

And the default install of Ubuntu doesn't have any runnign aplicatiosn that would respond to incoming network connections, so a firewall isn't required either. You only need to setup a firewall if you install some server software that you need to limit more precisely than that server's own configuration allows, or if you want to restrict what snetwork services users are able to connect to. If you need to setup a firewall then I recommend using UFW (or GUfw if you want a graphical tool). Whatever you sue, the firewall itself is built into Li nux so the tools you use are just tools for configuring that built-in firewall.

---

### Post by ndmp on 2010-02-12
Ubuntu comes with a standard linux firewall, I think. It's an all round secure OS.

---

### Post by fmfrisch on 2010-02-12
Linux comes with the the very secure iptables firewall. Ubuntu has on top of that added UFW which is an application to make iptables configuring easier. To this there is a nice GUI called gufw. Found in hte standard repositories. I suggest you add that if you want to mess around with hte firewall. However, it is perfectly safe as it is now without changing anything.

As for antivirus it is completely necessary for Ubuntu itself. But for windows files etc it can be nice if you are dualbooting. I've also heard that windows viruses may in certain cases work under wine. Not sure about that though. [Here's]("https://help.ubuntu.com/community/Antivirus") ubuntu's official page on antivirus in the documentation

---

### Post by 3rdalbum on 2010-02-12
> **fmfrisch said:**
> As for antivirus it is completely UNnecessary for Ubuntu itself. But for windows files etc it can be nice if you are dualbooting.

Corrected for you.

There are no viruses on Linux and the Windows viruses don't run unless you explicitly try to run them on Wine - even then, most of them will not even run.

As for a firewall, Windows is insecure - it runs software that listens to incoming connections. Ubuntu does not have any software that listens to incoming connections that runs by default, so a default Ubuntu box without a firewall is exactly as hackable as one with a firewall. That is, not very!

Plus, most broadband modems and routers already contain a firewall that will protect your whole network.

---

### Post by fmfrisch on 2010-02-12
Geez, my bad. I missed the UNnecessary. Hope I didn't scare people!

---

### Post by bapoumba on 2010-02-12
Moved to Recurring Discussions.

---

