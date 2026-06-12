---
title: "kopete not seeing 3G connection"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Circus-Killer on 2008-07-24
I am currently using a 3G connection to connect to the Internet. Now I have this problem. Its become a problem recently that Firefox also doesn't see the 3G connection and assumes its offline. Luckily, with Firefox, its easy to switch back to online mode and it works fine.

However, in KDE, I noticed that neither Konqueror or Kopete can see my connection. And what's more, I have no idea how to fix the problem.

Any suggestions?

---

### Post by ApOgEEs on 2008-07-24
you may file the bug on [https://bugs.launchpad.net/](https://bugs.launchpad.net/) :)

---

### Post by SNuxoll on 2008-07-24
This is because your 3G connection is established as a dial-up interface, even though it's about as far from dial-up as you can get.  Unfortunately, network-manager, and applications that use it to check network status, does not detect this connection and it thinks you are offline.

EDIT: I have made a bug for this on launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/251393").

---

### Post by ApOgEEs on 2008-07-24
Seems like a big unresolved issue... but there is workaround. [https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/191889](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/191889)

---

### Post by Circus-Killer on 2008-07-24
Thanks guys,
This did the trick for me:
> Workaround: (make NM to be always online) ->
 add a non existing interface to /etc/network/interfaces, like:
iface eth1000 inet dhcp


---

### Post by Circus-Killer on 2008-07-24
apologies, but the solution above that i said worked for me, it didn't. :(

i guess this is where i go back to gnome, until the issue has been addressed.

---

### Post by SNuxoll on 2008-07-24
The issue still exists in GNOME, it's a fault of NetworkManager, not KDE....

---

### Post by Circus-Killer on 2008-07-24
> **SNuxoll said:**
> The issue still exists in GNOME, it's a fault of NetworkManager, not KDE....

you are right in that it is network manager.

the reason i said im going back to gnome is because, with kde, most of the apps use network manager to determine if there is a connection and thus, they do not work.

the only program i have had a problem with in gnome is firefox, which you can easily fix. no other app in gnome has given me the same problem. however, in kde, most applications seem to suffer from this problem.

thats why im gonna just stick to gnome, and hopefully by 8.10 (Ibex) the issue will be sorted, and i will be able to choose my Desktop Environment without worrying about the effects of this damn network manager bug.

---

