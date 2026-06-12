---
title: "Starting the red5 server at boot time with Ubuntu server"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by IslandBill on 2014-04-21
Hi folks,

I've perused some of the advice on here about this and in other places as well.  It's all garbage, and some of it is even spam.  There is a very simple way to start red5 or any daemon which already has a start/stop/restart script in the /etc/init.d/ directory (like red5 does):

# update-rc.d red5 defaults

You should see something like:
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/red5 ...
   /etc/rc0.d/K20red5 -> ../init.d/red5
   /etc/rc1.d/K20red5 -> ../init.d/red5
   /etc/rc6.d/K20red5 -> ../init.d/red5
   /etc/rc2.d/S20red5 -> ../init.d/red5
   /etc/rc3.d/S20red5 -> ../init.d/red5
   /etc/rc4.d/S20red5 -> ../init.d/red5
   /etc/rc5.d/S20red5 -> ../init.d/red5


If you see that, you're good.  Do a reboot and test to make sure.

---

