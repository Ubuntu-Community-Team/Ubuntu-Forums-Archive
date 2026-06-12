---
title: "Mysqli problems...."
date: 2010-07-06
forum: Programming Talk
---

### Post by medic2000 on 2010-07-06
Hey guys i am watching some PHP videos from 2007. They are great but i have a problem. They are using normal mysql for querying databases. Everyone says mysqli is better but everyone still uses the old mysql. And i dont know the equivalent of them.

What are you suggesting. Should i use the mysql too?

---

### Post by medic2000 on 2010-07-07
No one has solution to this?

---

### Post by Compyx on 2010-07-07
I have used both, and I prefer the newer mysqli over mysql. Mysqli allows for an OO approach to querying databases, which leads to cleaner code (IMHO). That said, these days I prefer to use PEAR's MDB2 module, which further abstracts the code you write and allows you switch database backends (mysql, mysqli, postgresql, sqlite, etc) without the need to rewrite a lot of code.

From what I've read on the internet, mysql seems to perform better than mysqli with simple, hard-coded queries, but I'd go for cleaner code rather than performance. Things that start out simple often end up becoming more and more complex, so you might end up having to rewrite mysql-based code into mysqli/PEAR::MDB2 code. If you do need extra performance, you can always look into stuff like memcached and perhaps rewriting bottlenecks in C or C++.

---

