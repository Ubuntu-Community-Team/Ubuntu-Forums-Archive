---
title: "Networking doesnt work :("
date: 2013-02-21
forum: New to Ubuntu
---

### Post by Project ICE on 2013-02-21
root@bt:~# /etc/init.d/networking start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
networking stop/waiting
root@bt:~# start networking
networking stop/waiting
root@bt:~# networking waiting
networking: command not found
root@bt:~# start networking waiting
start: Env must be KEY=VALUE pairs



What did i do wrong?

---

### Post by steeldriver on 2013-02-22
AFAIK the recommended method for service start is

```
sudo service networking start
```However depending on what version of Ubuntu you are using, networking may be handled by the network-manager service instead:

```
service network-manager status
```in which case there may be nothing for 'networking' to do (i.e. /etc/network/interfaces contains no interface definitions aside from the loopback interface - in that case iirc the networking service will not start even if told to do so)

---

