---
title: "ddclient error on restart (dyndns)"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-13
I installed ddclient in ubuntu desktop 8.10 using synaptic package manager. I entered my info an installed. I did gksudo gedit /etc/ddclient.conf

I set my .conf too this

daemon=240
pid=/var/run/ddclient.pid
use=web, web=checkip.dyndns.org/, web-skip=IP Address
protocol=dyndns2
use=if, if=eth0
server=members.dyndns.org
login=correct
password='correct'
mydnshostname

I tried to restart ddclient using this in terminal

sudo /etc/init.d/ddclient restart

I received this error -

*Restarting Dynamic DNS service update utility ddclient
WARNING: skipping host: Address: 'login=' is an invalid login.

Any help with this would be much appreciated.

---

