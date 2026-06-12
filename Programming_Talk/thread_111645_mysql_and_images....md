---
title: "mysql and images..."
date: 2006-01-02
forum: Programming Talk
---

### Post by grim918 on 2006-01-02
i have quick noob question. i was wondering if images can be loaded into a database. i dont think that they can but i was just wondering.

---

### Post by Neeko on 2006-01-02
Yes they can, as Binary Large Objects, or BLOBs. However some consider it poor style, as it creates huge tables. As an alternative, I have stored the full path to an image in a table column rather than th e image itself.

---

