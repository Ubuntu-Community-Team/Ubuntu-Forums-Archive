---
title: "Wireless Networking Issue"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by philpense on 2013-05-21
Have run 12.04 from USB drive for months.  This day it is installed to the machine and fnd an issue with the wirless icon n the tray.  Instead of showing wireless network only wired networks are shown
Wired Network
Wired Connection 1
Disconnect
VPN Connection

How can one trouble such an issue? Guidance sought.

---

### Post by Tjkhan on 2013-05-21
did u try "additional drivers"? shows anything about wireless?

---

### Post by squakie on 2013-05-21
Post the outputs of the following:

Lshw -c Network

Lspci

Ifconfig

Iwconfig

Put each of the outputs inside code tags so we can see each group but not need to look through a long post.

Those are supposed to be lower case "l"'s

---

### Post by philpense on 2013-05-23
Much thanks for the timely reply.  Just realized that I turned off the hardware switch for the wireless adapter.  This problem is solved but I now find that my USB mouse is not recognized.  Seeking guidance on how to troubleshoot this.

---

