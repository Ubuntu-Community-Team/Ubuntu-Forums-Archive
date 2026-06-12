---
title: "How can I install a Linksys WRT150N-RM?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-09-27
I just received a Linksys WRT150N-RM wireless router and am unsure how to set it up with Linux.  Normally I would first set it up in Windows to make sure it works but Windows has died on my computer and I only have Linux to work with.  
It came with an install disc but there are no instructions on how to set it up with anything other than Windows.  
My primary concern is not only getting it work correctly as a wired router, but also to disable or encrypt the wireless since I do not need the wireless feature yet.

---

### Post by hyper_ch on 2008-09-27
setting up the router should be no problem.

Get a ethernet cable, connect the router and your computer with the ethernet cable, then run

```

sudo /etc/init.d/networking restart

```
(Just to make sure we get a good ip address)

then run
```

ifconfig

```

You should get something like this:

```

hyper@xubi:/home/svn/uvc/trunk$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:54:c7:ab
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe54:c7ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:705748 errors:0 dropped:388945008869 overruns:0 frame:0
          TX packets:708501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:540770028 (540.7 MB)  TX bytes:400171881 (400.1 MB)
          Interrupt:253

```

The important part is this here:  inet addr:10.0.0.10

Yours is very likely to be: 192.168.0.xxx

So take the first 3 bundles of digits and replace then xxx with a 1. In my case: 10.0.0.1, in yours very likely 192.168.0.1.

Enter that into the browser and you should get a login screen for your router.

Then you can set it up accordingly. If you change network details (like from using 192.168.0.xxx to 10.0.0.xxx) you need to run sudo /etc/init.d/networkring restart again.

---

### Post by curiousnoob on 2008-09-27
So am I correct in assuming that there is nothing vital on the installation disc and that all the features can be accessed directly through a web browser?

---

### Post by hyper_ch on 2008-09-27
routers - and all the linksys ones I have used so far - are normally administrated through the webinterface.

---

