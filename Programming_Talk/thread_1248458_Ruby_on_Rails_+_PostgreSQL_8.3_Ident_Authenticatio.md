---
title: "Ruby on Rails + PostgreSQL 8.3: Ident Authentication Failed."
date: 2009-08-24
forum: Programming Talk
---

### Post by infernus_crusher on 2009-08-24
Whenever I run script/server and go to one of my views on localhost:3000 it always gives me an Ident Authentication Failed if I use the following setup.

Username: postgres
Password: p

I have created user "postgres" with password "p" in PostgreSQL using the CREATE USER and ALTER USER commands respectively but it still doesn't work. However, if I use my Ubuntu user account and password it works.

Any ideas why?

---

### Post by Copernicus1234 on 2009-08-24
Just follow a guide: [http://wiki.rubyonrails.org/database-support/postgres](http://wiki.rubyonrails.org/database-support/postgres)

---

