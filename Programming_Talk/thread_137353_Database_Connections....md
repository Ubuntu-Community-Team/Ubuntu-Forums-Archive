---
title: "Database Connections..."
date: 2006-02-27
forum: Programming Talk
---

### Post by grim918 on 2006-02-27
I was wondering if it is a good programming habit to connect to two different databases in a single script. I want to create a seperate database which will hold information about failed logins and other types of information such as keeping track of who has viewed certain webpages. I want to keep this information in a separate database, but i don't know if it's a good idea. Will this create any problems, please let me know.

---

### Post by LordHunter317 on 2006-02-27
Why in the world you want to keep that in a seperate database?

Applications that connect to two DBs aren't a bad idea *per se*, but your idea sounds like a rediculously bad one.

The only valid reason I could think of is if the authentication data is shared among multiple applications but the page data is not, in which case, it's perfectly fine.

---

### Post by grim918 on 2006-02-27
ok thankz again. I just wondering if that was a good programming habit. Thank you.

---

