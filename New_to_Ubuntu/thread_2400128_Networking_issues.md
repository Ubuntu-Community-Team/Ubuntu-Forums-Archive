---
title: "Networking issues"
date: 2018-09-03
forum: New to Ubuntu
---

### Post by Nezmin2 on 2018-09-03
Guy's, I have been attempting to set up a Ubuntu Server (18.04) VM using VirtualBox. Out of the box, no ip4 address shows on the NIC. I have tried setting a NAT on adapter 1 and a Bridged on adapter 2, as well as just a bridged. No matter which what, the same issue shows up. I then found instructions on using netplan, but it still doesn't change things. I am very confused and frustrated. I would love to know what I'm doing wrong. Also, the adapter for the host is set to 192.168.1.30/27, however, after looking through the cloud init file, it show's 192.168.1.24/27.

---

### Post by Nezmin2 on 2018-09-04
Problem solved... I found the instructions on Netplan and added my settings into the 50-cloud-init.yaml file (See attached image) and rebooted and everything worked. [ATTACH=CONFIG]280991[/ATTACH]

---

### Post by QIII on 2018-09-04
Hello!

Would you care to share your solution for the benefit of the community?

Thanks!

---

