---
title: "Connect to Windows 8 via Remmit"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by kurasdan on 2014-09-14
I've just installed Ubuntu 14.04 and the Remmina on an older laptop and am attempting to start a remote desktop session with my windows 8.1 desktop machine.  Windows is configured to accept rdp requests, BitDefender firewall passes rdp by default. I've entered my Windows credentials into Remmina, including the IP address of the Windows machine.  Remmina attempts to connect, but times out.  I've also tried with Vinagre with the same results. And I can't find the known_desktop folder whose deletion is said to resolve this problem. I'm a retired IT specialist and well acquainted with Windows Remote Desktop on Windows machines.

---

### Post by nerdtron on 2014-09-14
Just to rule out the firewall issue, try disabling the firewall on windows completely and let's see if Remmina can connect.

---

### Post by kurasdan on 2014-09-15
I tried again this morning and for some reason it worked.  Both the Ubuntu and Windows machines were rebooted, which probably solved the problem. Anyway, I've spent 30+ years in electronics design, software development, and network admin and have learned "if it ain't broken, don't fix it"

Thanks again
Dan Kuras

---

