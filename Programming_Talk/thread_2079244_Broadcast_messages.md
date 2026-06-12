---
title: "Broadcast messages"
date: 2012-11-01
forum: Programming Talk
---

### Post by VVovchenko on 2012-11-01
Hello!!!

I'm writing server and found a strange problem.
When server send broadcast message it should recieve it. When we running server on ubuntu-desktop everythink all right. But when I run it on ubuntu-server I found that my application didn't recieve broadcast messages from itself.

ubuntu-server 10.04

```

# ufw status
Status: inactive

# uname -a
Linux astorex 2.6.32-44-server #98-Ubuntu SMP Sep 24 17:41:33 UTC 2012 x86_64 GNU/Linux

# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0

```

May be some other firewall is installed by default? Or maybe someone faced a similar problem?

---

