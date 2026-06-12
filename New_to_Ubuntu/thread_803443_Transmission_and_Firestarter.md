---
title: "Transmission and Firestarter?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by m_ad on 2008-05-22
Is there a way to setup Transmission to only work with 1 or 2 ports, so that I can allow that port in Firestarter?

When running Transmission, I see A BUNCH of activity in Firestarter from random ports. How do I set this up correctly?

Thanks..

---

### Post by bodhi.zazen on 2008-05-22
Looks like you will need to configure firestarter to be more permissive, allow all outgoing connections. Keep incoming traffic blocked by default.

[http://forum.transmissionbt.com/viewtopic.php?t=4814](http://forum.transmissionbt.com/viewtopic.php?t=4814)

Otherwise you may need to look at an alternate client.

---

### Post by nowshining on 2008-05-22
or go into the apps settings and find an option not to use random outgoing ports & pick one port - alas if u want people to download from u, u'll need to also pick an incoming port and allow incoming (all) on that port.

---

### Post by bodhi.zazen on 2008-05-22
> **nowshining said:**
> or go into the apps settings and find an option not to use random outgoing ports & pick one port - alas if u want people to download from u, u'll need to also pick an incoming port and allow incoming (all) on that port.

I am not an expert on transmission, but from what little I saw of the documentation it looks as if that configuration of transmission (restricting to a single port or range of ports) will limit the download speed.

---

### Post by nowshining on 2008-05-22
> **bodhi.zazen said:**
> I am not an expert on transmission, but from what little I saw of the documentation it looks as if that configuration of transmission (restricting to a single port or range of ports) will limit the download speed.

oh, then that program is a hog on ports & I would never use it if that's the case. 'cauze it could knock-out use of used ports.

---

### Post by Paqman on 2008-05-22
> **nowshining said:**
> oh, then that program is a hog on ports & I would never use it if that's the case. 'cauze it could knock-out use of used ports.

I pretty much doubt that.

---

### Post by nowshining on 2008-05-23
lol the problem with randomness is of course the random part esp. if wanting to block certain outbound ports or esp. worse incoming ports.

---

### Post by amaroKer on 2008-05-23
You can set Firestarter to allow all outgoing connections safely.  Set 'Outbound Traffic Policy' under the Policy tab to **Permissive by Default**
The only thing you need to worry about in this situation is:
1) Malicious code running on your Linux box (nope.)
2) Applications that "call home". (nope.)
You must then set a port for Transmission to use in the program, as well as in Firestarter, and in your router (if applicable).  This configuration works for me.  Except that I use Deluge instead of Transmission because it seems MUCH faster and has a spiffy speed graph!

---

