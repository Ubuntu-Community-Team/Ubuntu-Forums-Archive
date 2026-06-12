---
title: "How to locate and delete trash installs?"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-18
In attempting to add a 8187 adapter driver, I installed many items.

They are trash and not needed.

How can I conduct a search and destroy mission?

---

### Post by dniMretsaM on 2012-04-18
How did you install them?

EDIT: 1000th bean!!!

---

### Post by 2F4U on 2012-04-18
The file /var/log/apt/history.log has a history of all items installed by apt. But this requires that you installed the software by apt and not, for example, by manually compiling it.

---

