---
title: "anybody know of a ESXi forum???"
date: 2008-10-16
forum: Other OS Talk
---

### Post by kc2bxn on 2008-10-16
Ok i've been playing with ESXi.
Thats a very nice setup, but for free stuff from VMware they are not helpful.
Does any one know the nitch forum that i'm looking for??


thanks :)

Ian

---

### Post by kk0sse54 on 2008-10-16
There's a virtualization sub-forum here on Ubuntu forums and here's a link to thet  Vmware forums with an  ESXi sub-forum [http://www.vmwareforum.org/YaBB.pl?board=esxi](http://www.vmwareforum.org/YaBB.pl?board=esxi)

---

### Post by teryret on 2008-10-23
How well does local access work in ESXi?  What I mean is, I'm about to buy a new workstation, and I'm going to need to run both Ubuntu ('cuz I wanna) and Windows (wine doesn't support Visual Studio...), and I'd really like to see "bare metal" performance in both machines.  The question is, in ESXi is there a local GUI at all (similar to how workstation and player work)?

Also, do you happen to know if the free version of vmware converter can convert to ESXi?

---

### Post by self-defence on 2008-10-26
ESXi has almost no local GUI. You can set the IP address and shutdown/reboot the server and you can even login to the support console(it is not recommended). But the one thing that can't be done is interface with the VMs locally. You can do this via VMWare Infrastructure Client witch unfortunately only exists for Windows. As fare as performance goes it's grate.
As for the converter I was able to convert a non VM WinXP into ESXi and a few VMs from VMWare Workstation.

Best regards

---

