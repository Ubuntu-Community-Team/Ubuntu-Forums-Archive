---
title: "Install DHCP on Ubuntu server?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by BUNAC on 2008-10-30
Hi guys!
I've been searching round for a while but I can't find an up-to-date description of how to setup Ubuntu Server as a DHCP server.

I've installed Ubuntu Server 8.04 (with the GUI as I'm a Windows tech!! - don't curse me I'm trying to convert :)).

I'm basically trying to set up Ubuntu as a wireless internet gateway for a internet cafe so it needs to serve IP configurations to a variety of wireless clients.

Can anyone recommend a starting place for me? :)

Cheers
Tom

---

### Post by nhasian on 2008-10-30
Hello Tom,

see if this helps:

[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

---

### Post by northern lights on 2008-10-30
Install the packages *[dhcp3-server]("http://packages.ubuntu.com/search?keywords=dhcp3-server&searchon=names&suite=intrepid&section=all")* or *[dhcp3-server-ldap]("http://packages.ubuntu.com/search?keywords=dhcp3-server&searchon=names&suite=intrepid&section=all")* (able to use LDAP as backend). Their available from the universe repos:

```
sudo apt-get install dhcp3-server
```

---

### Post by BUNAC on 2008-10-30
Hello,
Thanks for your responses, I've managed to install and I think configure the DHCP server but unfortunately it won't start!

When trying to restart the server I get the following errors:

Stopping DHCP server dhcpd3 [fail]
Starting DHCP server dhcpd3 [fail]

It must have installed OK as I can edit the config files.

Any ideas guys?

Thanks for your help
:)

---

### Post by Dr_Muesli on 2008-11-08
I've been struggling with the same problem for the last week and I think I found out how to do it. 
Please quote the contence of /etc/dhcp3/dhcpd.conf and /etc/network/interfaces and /etc/default/dhcp3-server
Maybe I can help, but it is also difficult for me, because this is the first server I am building.:confused::)

Grtz,  Erik

---

