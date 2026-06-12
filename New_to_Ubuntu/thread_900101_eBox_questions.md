---
title: "eBox questions"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-08-25
Hi.  I have just started using eBox, and I have a few questions:

-This is a little embarrassing, but what must I type into the terminal to find out my IP address?  It is assigned via DHCP by my router.

-How exactly do install additional modules?

-If I install a module, will eBox automatically start that service for my server?  For example, if I installed the Squid module, would squid automatically be installed and started?

Thanks in advance!

I am using 8.04 installed on a Vbox virtual machine.

EDIT: One more basic thing I should probably know.  What commands do I use to:

-shutdown
-restart

---

### Post by 67comet on 2008-08-25
To find your IP:
ifconfig

once you've done that it will show you all your network devices. Mine is eth0, so it would be:
ifconfig eth0


To restart:
sudo shutdown -r now


To shutdown:
sudo shutdown -h now

Hope it helps, I love my Ubuntu Servers (HUGS them)

---

### Post by pi.boy.travis on 2008-08-25
Awesome.  Thanks!  I would like to get some running in the near future for my Church Youth Group website to replace our not so great (and expensive) hosting service.

---

