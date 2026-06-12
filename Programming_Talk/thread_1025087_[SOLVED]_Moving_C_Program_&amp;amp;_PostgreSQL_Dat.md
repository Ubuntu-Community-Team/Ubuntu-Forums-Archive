---
title: "[SOLVED] Moving C Program &amp;amp; PostgreSQL Database"
date: 2008-12-29
forum: Programming Talk
---

### Post by rich1939 on 2008-12-29
I'm developing a C/GTK+ program that also uses the PostgreSQL database. I'd like to move both the program and database to another computer from time to time...but although I am able to move the program, I can't seem to find where PostgreSQL stores the database. I tried "find" to locate it by name, but didn't get any hits. Does anyone know where the database is stored?

---

### Post by Quikee on 2008-12-30
> **rich1939 said:**
> I'm developing a C/GTK+ program that also uses the PostgreSQL database. I'd like to move both the program and database to another computer from time to time...but although I am able to move the program, I can't seem to find where PostgreSQL stores the database. I tried "find" to locate it by name, but didn't get any hits. Does anyone know where the database is stored?

Why not backup the database (via. pg_dump) on one computer and restore on the other computer. See [here]("http://www.postgresql.org/docs/8.0/interactive/backup.html") for the procedure.

---

### Post by rich1939 on 2008-12-31
> **Quikee said:**
> Why not backup the database (via. pg_dump) on one computer and restore on the other computer. See [here]("http://www.postgresql.org/docs/8.0/interactive/backup.html") for the procedure.

Duh! Why didn't I think of that! Great answer.

Thanks a lot.

---

