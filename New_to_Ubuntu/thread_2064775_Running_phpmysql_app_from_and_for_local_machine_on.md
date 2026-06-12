---
title: "Running php/mysql app from and for local machine only"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by bbosa on 2012-09-30
Hi all,

My organization needs to run a sensitive database application on a PHP/MySql platform. While I'd like to have it available over the LAN I don't trust our network security or local expertise enough to secure the network. So the option we are pursuing is to have the application running on a single laptop running Ubuntu with full-disk encryption.

I want to ensure that the LAMP stack will only serve local requests (originating from the laptop) and that it's secured against hacking. Is it best to use standard Ubuntu or Ubuntu server?

And what's the best way of ensuring that the installation is secured from hacking and won't serve an external request?

I don't mind hiring a consultant to do configurations if necessary. I'm just looking for some help to know what is involved.

Thanks

---

### Post by spottraining on 2012-09-30
Disable in MySQL config external connections
And with firewall You can play so, that only 80 port is open and accepted mashines are only from internal networks.

I am recomending Zentyal server - it is also Ubuntu based, but in one place You can handle all what needed.

---

### Post by bbosa on 2012-10-01
Thanks spottraining,

I see Zentyal is at a cost of $50/month which seems unnecessary for our purposes of a single application running for local usage only. Is there another system you would recommend for this purpose. Is virtualization something I should consider?

---

### Post by Dragonbite on 2012-10-02
> **bbosa said:**
> Thanks spottraining,

I see Zentyal is at a cost of $50/month which seems unnecessary for our purposes of a single application running for local usage only. Is there another system you would recommend for this purpose. Is virtualization something I should consider?

Look at [Zentyal.org]("http://www.zentyal.org"), which is their free Community based version.  

They provide an ISO of Ubuntu Server with the Zentyal (formerly ebox) system pre-installed.  Version 3.0 uses Ubuntu Server 12.04 and version 2.? is built in Ubuntu Server 10.04.  I think they also offer a VM image as well.

I just installed it over the weekend and do recommend them for people not yet ready for a command-line only server interface (like me).  I am using it as a gateway/firewall (2 NICs, one outside to the modem, one to the internal network) and the LAMP server works but I haven't done anything with it yet.  I installed it on the system because I don't want any chance my external line comes in without going through Zentyal.  Eventually I am hoping to install DansGuardian content filter as well.

The interface makes it easy to manage a lot of services; file sharing (Samba), web server (LAMP), DNS, DHCP (handing out IP addresses), routing (one NIC to another), firewall, LTSP (thin clients), and more.  Plus, you don't have to install all of the packages, just the ones you like or install a pre-selected group in one of their packages.

It provides a means to manage the system through a web interface you can access internally (https://<ip of server>:443) and I made sure my external firewall leaves nothing open.

The pay-for company are the sponsors and developers similar to Canonical is to Ubuntu.

---

