---
title: "port forwarding with speedtouch router"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-13
Hi. Looking at Speedtouch site, it seems port forwarding isn't available for linux users. Anybody know any different.
M

---

### Post by cariboo on 2008-11-13
Networks don't care what OS is running. Have a look at this page:

[http://chelydra.dyndns.org/st_resources/](http://chelydra.dyndns.org/st_resources/)

More terminal practice. :)

Jim

---

### Post by irish66 on 2008-11-14
Thanks a lot, will try to do it at some stage.
alhough according to [http://portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch530/default.htm](http://portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch530/default.htm)
I need to set up a static ip addy,and it doesn't show how to do it
with linux.
M

---

### Post by Joeb454 on 2008-11-14
Usually this is all done via the router's web interface.

I know mine is anyway

---

### Post by superprash2003 on 2008-11-14
you can create static ip via the command line way [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html) or the GUI way ( if you arent running ubuntu 8.10)[http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html](http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html)

---

### Post by irish66 on 2008-11-15
quote "Step 1 : Go to the Terminal(Applications->Accessories->Terminal)
Step 2 : Then type sudo gedit /etc/network/interfaces
Step 3 : Now the interfaces file should open on gedit.
Step 4 : Now look for the line
iface eth0 inet dhcp"

All i get is
lo
iface lo inet loopback

M

---

### Post by irish66 on 2008-11-15
Well. still having router problems. But I remembered I also had a netgear modem ie not a router. So switched over to the modem, choose direct connection, and lo and lo and behold I'm on active.
M

---

