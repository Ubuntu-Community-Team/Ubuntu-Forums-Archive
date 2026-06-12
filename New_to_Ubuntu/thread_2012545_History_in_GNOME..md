---
title: "History in GNOME."
date: 2012-06-29
forum: New to Ubuntu
---

### Post by zozza on 2012-06-29
History is located in .bash_history.

However, I am wondering if it is backed-up anywhere else.

In other words: if I delete .bash_history, can I display my historical commands from somewhere else for example a backup file?

Thanks.

---

### Post by southerngeek on 2012-06-29
Any commands you've run with sudo are also stored in /var/log/auth.log.

---

### Post by oldos2er on 2012-06-29
And /root/.bash_history too if I'm not mistaken.

---

### Post by southerngeek on 2012-06-29
> **oldos2er said:**
> And /root/.bash_history too if I'm not mistaken.

I think that's just for when you're actually logged in as root. On mine it doesn't remember sudo commands done from within a normal account.

---

