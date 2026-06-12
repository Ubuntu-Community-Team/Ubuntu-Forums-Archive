---
title: "Databases compound key vs composite key?"
date: 2013-04-01
forum: Programming Talk
---

### Post by binaryperson on 2013-04-01
Hello. Can someone please explain, in simple terms, what are the differences between a compound key and a composite key? Please give examples of both if possible.

---

### Post by r-senior on 2013-04-01
See:

[http://en.wikipedia.org/wiki/Compound_key](http://en.wikipedia.org/wiki/Compound_key)
[http://dba.stackexchange.com/questions/3134/in-sql-is-it-composite-or-compound-keys](http://dba.stackexchange.com/questions/3134/in-sql-is-it-composite-or-compound-keys)

It's a subtle distinction typical of a homework or exam question.

---

### Post by binaryperson on 2013-04-01
Thanks.

---

### Post by slickymaster on 2013-04-02
Compound keys occur when the DB schema specifically uses more than one column to form the primary key, composite keys are generated when no PK (primary key) is designated in the database at time of import.

---

