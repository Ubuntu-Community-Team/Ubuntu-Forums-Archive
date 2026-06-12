---
title: "Ubuntu VDI on Ubuntu Server with Zero client"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by fusionp on 2012-04-10
Hi all, I'm very new to Ubuntu, I've virtualized windows desktops with vmware view in the past and was wondering if the same can be done usuing Ubuntu only software, i.e. ubuntu server as the hypervisor, publishing ubuntu desktops? If this can be done can the VDI's be conencted to with zero client or would it have to be thin client?

Any help much appreciated!

---

### Post by Cheesemill on 2012-04-10
Take a look at LTSP (Linux Terminal Server Project).

It can be installed using the Alternate installation CD.

[http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

### Post by fusionp on 2012-04-10
Thanks, I've done a quick search on LTSP, I see a lot of info for thin-clients, but can't see anything for zero clients. Do you/anyone know if there is a true zero client that will work with LTSP? The only thing I found was zero-client that needed another network appliance to PXE boot the "zero"...so not really a zero..

Thanks for the links!

---

