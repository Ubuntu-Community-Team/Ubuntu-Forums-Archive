---
title: "3COM 3C905X Ethernet card not working"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by SlappyPappy on 2008-08-19
I've searched through the forums and can't quite figure out how people are fixing this problem. I've poured over threads that go on forever but I still don't know what the process is to fix the card so it will work in Ubuntu.

If someone can give me the shortened version I'd be most appreciative. Thanks.  :)

---

### Post by SlappyPappy on 2008-08-19
Okay, so I'm working my way through this.

The first thing I did was to add:

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

to /etc/network/interfaces

I rebooted and still no love. The work continues....  :guitar:

---

### Post by SlappyPappy on 2008-08-19
Hey hey! All fixed up and ready to roll.

Apparently the drivers are messed up on the 3Com card and need to be changed via a utility found here:

[http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3C905B-TX&order=desc](http://www.3com.com/products/en_US/result.jsp?selected=all&sort=effdt&sku=3C905B-TX&order=desc)

The 3c90X2.exe file is the one you want.

This cat here gives you good directions.

[http://ubuntuforums.org/showthread.php?t=503194&page=2](http://ubuntuforums.org/showthread.php?t=503194&page=2)

Basically you just have to autoconfigure the card and it will be recognized now in Ubuntu Hardy.

Sweet!

---

