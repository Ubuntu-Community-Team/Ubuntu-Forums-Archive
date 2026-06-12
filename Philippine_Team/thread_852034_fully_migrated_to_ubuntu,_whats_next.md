---
title: "fully migrated to ubuntu, whats next?"
date: 2008-07-07
forum: Philippine Team
---

### Post by sagumay on 2008-07-07
now that ubuntu succesfully invaded my home PC "lol", gusto ko po rin sanang gamitin ubuntu sa work ko, kaya lang kelangan ko po ng equivalent ng mga program na'to sa linux. pa help naman po.

Remote Desktop Connection
Remote Administrator
HyperTerminal
Look@LAN or IP Scanner

PC ko lang po ang ubuntu the rest is Windows. Salamat po ng marami

---

### Post by jeffimperial on 2008-07-07
Remote Desktop Connection
**VNC** HowTo here [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

Remote Administrator
It depends on how you want to do it. UltraVNC is probably the easiest if you have the network bandwidth. Alternatively, it's not all that tough to set up an ssh server on it with Cygwin. If you want to really overengineer things, I *think* you could set up your Linux box as a Domain server with Samba, but that's a _lot_ of work.

HyperTerminal
**Minicom** seems to be a popular choice. It has an online [man-page here]("http://linux.die.net/man/1/minicom").
**gtkterm** has given others a satisfying go. [Wikipedia]("http://en.wikipedia.org/wiki/Gtkterm") knows, but not much, about it.

Look@LAN or IP Scanner
**[AutoScan]("http://www.gnomefiles.org/app.php/AutoScan")** is an application designed to explore and to manage your network. Entire subnets can be scanned simultaneously without human intervention. It features OS detection, automatic network discovery, a port scanner, a nessus client, a Samba share browser, and the ability to save the network state.

I'm sure the Community has much more opinion to offer :) I personally am not a sys admin, but I do a little (puny actually)...

---

### Post by sagumay on 2008-07-08
thanks.

---

