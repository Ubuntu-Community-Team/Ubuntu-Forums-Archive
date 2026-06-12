---
title: "sqlite3 python and keyword like"
date: 2009-10-29
forum: Programming Talk
---

### Post by jworr on 2009-10-29
normally I a query with a 'like' keyword would look like this:

select * from some_table where name like '%foo%'

but since I'm using a parameterized queries with python's database interface my query now looks like this:

select * from some_table where name like ? 

My issue is, I don't know how to specify the %.  I've tried %?% and '%?%' but it doesn't work.  Does anyone know how to do this?

---

### Post by jworr on 2009-10-29
Never mind, I just added the %'s to the parameter

---

