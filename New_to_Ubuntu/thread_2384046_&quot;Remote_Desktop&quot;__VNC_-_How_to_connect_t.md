---
title: "&quot;Remote Desktop&quot; / VNC - How to connect to Ubuntu"
date: 2018-02-01
forum: New to Ubuntu
---

### Post by jamapii on 2018-02-01
Hello,

How can I connect to an Ubuntu box with VNC, from ordinary Linux or an older Mac? Without changing settings on the Ubuntu box.

tigervnc cannot. cotvnc or Chicken of the VNC cannot. It seems almost no VNC viewer at all can connect, except for commercial software. No passwords, key files, or certificates are required then.

Example message:
```

 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7
 CConnection: No matching security types
 CConn:       No matching security types

```

Also, if it ever works, how can I get correct keyboard input? Last time I connected to an Ubuntu VNC, very long ago, the keyboard input was completely garbled by default, which is very unusual for VNC.

---

### Post by bonzini on 2018-02-02
Why would you want to use VNC to connect to a server?  A server usually doesn't run any kind of desktop environment.  Maybe you want to use ssh instead?

---

### Post by jamapii on 2018-02-02
OK, sorry I'm gonna change my wording: s/server/box/

I'm sure this applies to any Ubuntu box as of version 16.4

---

### Post by cariboo on 2018-02-02
You may need to install a different Desktop, as Unity does not work with remote desktops. Try XFCE or LXDE, both are available in the repositories

---

### Post by HermanAB on 2018-02-03
Bear in mind that VNC is mostly a Windows thing, is horribly insecure and will likely get your computer hacked shortly after you finally managed to get it to work...

Rather read the Snail Book: [http://www.snailbook.com/](http://www.snailbook.com/)

---

### Post by ionut23 on 2018-09-23
I use nomachine on my mac, so I installed nomachine server on Ubuntu (downloaded from [https://www.nomachine.com/download](https://www.nomachine.com/download)).
Added my Ubuntu ip to my nomachine client on my mac, and I could connect to Ubuntu computer - working OK, (you need to consider that if your ubuntu computer has a monitor connected - it will display what are your doing when you are connecting remotely so I keep my Ubuntu computer with disconnected monitor)

---

