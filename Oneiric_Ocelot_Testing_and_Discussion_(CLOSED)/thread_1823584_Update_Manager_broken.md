---
title: "Update Manager broken?"
date: 2011-08-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Sennaista on 2011-08-12
Excuse me if this has been posted before but Update Manager has been broken for the past 3 or 4 days. It does not update the software list when asked and it doesn't install what it already has in the list of updates either. It just crashes with Apport showing up.

Any explanations/solutions?

Thanks

---

### Post by Noz3001 on 2011-08-12
Indeed. I've just stuck to apt-get update and apt-get upgrade

---

### Post by mc4man on 2011-08-12
This is most likely the bug, no need to comment in, issue is known
[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/822913](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/822913)

Edit : and just fix released, upgrade should be avail.

---

