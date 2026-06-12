---
title: "Tablename?"
date: 2007-08-20
forum: Programming Talk
---

### Post by beckham on 2007-08-20
Hi,I want a variable table name in a procedure.I thought some IN parameters can be passed like procedure may receive a varchar table name or a number deciding which table to use for fetching data. Is it possible?

---

### Post by kidders on 2007-08-20
Hi there,

What language are you talking about? What sorts of tables?

---

### Post by frafu on 2007-08-22
Hello, 

The Accessibility forum being intended for discussions about Assistive Technology, I am moving this thread to a forum related to development. 

Have a nice day. 

Francesco

---

### Post by kidders on 2007-08-29
> **frafu said:**
> I am moving this thread to a forum related to development.Thanks. I suspected this thread wouldn't turn out to be accessibility-related. Beckham seems to have lost interest anyhow.

---

### Post by pmasiar on 2007-08-29
> **beckham said:**
> Hi,I want a variable table name in a procedure.I thought some IN parameters can be passed like procedure may receive a varchar table name or a number deciding which table to use for fetching data. Is it possible?

Is it SQL? You cannot have table name as parameter in prepared statement (it makes sense: how SQL can prepare statement if table name is not known? :-) )

You can substitute table name in string with SQL statement, but then you need to prepare statement again.

---

### Post by beckham on 2007-09-07
yes it's of MYSQL and thanks for the answer.

---

