---
title: "get root privileges in gtk apps"
date: 2006-12-18
forum: Programming Talk
---

### Post by scorpio2002 on 2006-12-18
Hi there! I'm developing a gtk2+ application and I'd like to know how do you prompt the user for root password... (this program needs to modify some memory registers...).

---

### Post by ciscosurfer on 2006-12-18
> **scorpio2002 said:**
> Hi there! I'm developing a gtk2+ application and I'd like to know how do you prompt the user for root password... (this program needs to modify some memory registers...).You can use **gksu** or **gksudo **(or** kdesu** for kde apps) to prompt the user to enter the administrative password.  [You can learn more about them here]("http://www.psychocats.net/ubuntu/graphicalsudo").

---

