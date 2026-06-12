---
title: "How can i find the version of citrix receiver i am running"
date: 2015-10-01
forum: New to Ubuntu
---

### Post by Ian_Selby on 2015-10-01
Hi All,

Very new to Ubuntu here, but I did manage to follow a guide to put together a custom distro a few years back to essentially build a deployment with locked down firefox and citrix receiver to be used as a thin client. However we need to renew our SSL certificate on our access gateway (netscaler) soon, and have to transition to SSL SHA2, however I have read somewhere that not all receivers are compatible with SHA2. A such I need to find out what version of the receiver we have installed on our builds and update them if necessary.

Being more of a windows user, I have no idea of how to determine the receiver versions installed on the Ubuntu boxes.

Any help appreciated.

Ian

---

### Post by NathanRodriguez on 2015-10-01
Try this:

[http://docs.citrix.com/en-us/receiver/linux/13-2/linux-command-line-parameters.html](http://docs.citrix.com/en-us/receiver/linux/13-2/linux-command-line-parameters.html)

Looks like it's:

wfica -version

---

