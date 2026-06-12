---
title: "FireStarter: New Bee : Not able to Start it"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by aprilmot on 2008-09-20
Hello all,
Hi I am new to Ubuntu.  I switched few weeks back from xp.  I am connected to internet via wireless lan.  I tried to install the firestarter and configure it to secure my laptop.  But unfortunatelly it is not running.  Please find the snapshot of the error it is prompting.

---

### Post by MegaJim on 2008-09-20
That error is due to there not being an active connection.  Firestarter can only make the rules of the firewall active when it finds an active connection.

Make sure you have checked "start on dial out" and that the correct network interface is selected.  Then connect to your network and the firewall should automatically start.

Also consider trying [Gufw]("http://gufw.tuxfamily.org/index.html"): firestarter is no longer being developed and Gufw looks very promising.

---

### Post by hyper_ch on 2008-09-20
Are you sure you need to alter the default firewall? What do you want to achieve with the modified firewall?

---

### Post by gandaran on 2008-09-20
Gufw firewall is a lot easier to configure [http://www.getdeb.net/](http://www.getdeb.net/) [http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/)

---

### Post by airtonix on 2008-09-20
Yes firestarter wont create rules for ethernet devices it cant see.

As far as firewall frontends go, I find that gufw is a poor substitute to firestarter.
it also doesnt have a way to enable simple internet sharing.

---

