---
title: "[SOLVED] re-installed now no internet, please help"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by wordmaster on 2008-05-11
I installed Ubuntu using Wubi for a triple boot, 98SE, 2000 pro, Ubuntu.

I did too many things wrong and did not know how to fix them, so I uninstalled, used ccleaner, got a nice clean uninstall and then re-installed.

On the first install, internet connection was there to start with and there were no problems.

On this install, I have so far been totally unable to connect to the internet. I am back in windoze writing this. 

I have a DSL always on hookup with a wire to my network card that does not need a username/password login. On the first install everything was found, automatically set up and no problems.

When I check to see if the net package is setup it tells me it finds it and it is OK.

It finds the network card at eth0. When I run pppoeconf it runs and I get this error;

"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem."

Needless to say the cables, etc. are OK as I am using them now in windoze. As far as I know there is no other process running.

Thank you for any help you can give.

---

### Post by spongedaddy on 2008-05-11
OK, this might be obvious, but have you tried administration > network > wired connection > properties? Set it to DHCP.

My internet connection with Hardy has been spotty at best. Setting this has fixed it.

Just my $.02.

---

### Post by wordmaster on 2008-05-11
I had tried that, but it didn't appear to work correctly. So I went back in, tried it again and now I have internet. Thank you!

---

