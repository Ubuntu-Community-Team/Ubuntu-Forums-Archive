---
title: "[SOLVED] MySQL:  How to sync primary keys across tables?"
date: 2008-11-29
forum: Programming Talk
---

### Post by Igniteflow on 2008-11-29
Not sure if a MySQL question belongs in the programming section, apologies if this is wrong sectioned.

I have five tables that I setup and populated in MySQL, each of which is assigned a primary key which is shared across some of the tables (foreign key?  Sorry, I'm new to this).  I want to link the primary keys which are the same so if they are updated in one table then they will be updated in all their other occurrences.  For example I have a user_id column in the user table which also appears in the user registration table.  If I update the number in the user table I want it to automatically update in the user registration table.
Any suggestions?

---

### Post by pmasiar on 2008-11-29
> **Igniteflow said:**
> I want to link the primary keys which are the same so if they are updated in one table then they will be updated in all their other occurrences.

You can do such updates within single transaction, but why? Once key is assigned, it should never be changed. If you need to change some kind of user ID often, create another machine-user-id, which never changes.

Updating IDs is hassle with no business value, and makes harder to compare data from different timestamps. 

You don't need it, and if you do, likely your design is wrong.

---

### Post by Igniteflow on 2008-11-30
Thanks for the reply pmasiar.  I've since realised that the primary keys update automatically across the tables and there's no need to manually sync them.

---

### Post by drubin on 2008-11-30
I agree with **pmasiar** there is no value in having a primary key that changes.

---

