---
title: "MySQL auto-increment key updating help."
date: 2008-06-19
forum: Programming Talk
---

### Post by swordsmith on 2008-06-19
Hi all,
So I made a table with auto-incrementing IDs as primary keys. However, if I delete an entry from the table, the IDs stay the same for all entries. I'm wondering whether there is a way to make the table so that when something's deleted, the IDs automatically shift to correct the change?

Thank you all very much.

---

### Post by LoneWolfJack on 2008-06-19
if you want to rearrange the id's you will have to do it by hand. ids are kept for the purpose of crosslinking.

also, there is no reason for keeping the ids in line short of the pretty looks.

---

