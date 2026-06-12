---
title: "USB to serial driver for Ubuntu 14_04"
date: 2014-09-26
forum: New to Ubuntu
---

### Post by Heena123 on 2014-09-26
hi all,

i am beginner with Linux and now i just purchase bafo product BF 810 Cable for my testing purpose .

I already download Linux version driver but  it not installed properly and its in Redhat version .

So may be i was thinking that  "that's why its not install relatively"

so please give some other option for Ubuntu 14_04 and also  FTDI cable is more compatible with Linux and also support Linux 12_04 and higher version


please guide me

---

### Post by Vladlenin5000 on 2014-09-26
Hi, welcome.

That cable, as any other Prolific based are natively supported since a very long time ago.

---

### Post by Rob Sayer on 2014-09-26
This is apparently the driver you want:

[http://manpages.ubuntu.com/manpages/saucy/man4/uplcom.4freebsd.html](http://manpages.ubuntu.com/manpages/saucy/man4/uplcom.4freebsd.html)

and you can check if you already have it with synaptic ... that'd be easiest.

Also, remove the driver you installed for it before, and delete that ppa from your sources list.

---

