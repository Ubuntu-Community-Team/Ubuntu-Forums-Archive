---
title: "Problems with JDEveloper"
date: 2007-04-15
forum: Programming Talk
---

### Post by mehaga on 2007-04-15
Hi all,

I tried to follow Oracle Application Server tutorial for developers, but I got some errors after few steps. I didn't see anyone else complain about this, so I thought it might be because I'm testing on Ubuntu...

One of the steps in tutorial is creating entities (EJB 3) from tables, using a wizard. It should create 5 - 6 classes, one for each table in SRDemo schema. However, it only creates one, and as soon as it encounters a table that has multiple columns set as primary key, it stops. I tried with another schema, just to make sure it is not the schema that causes the problem, but JDeveloper then created 2 instead of of 8 classes, and stopped generating them after it created a PK class for one of the tables, just like it did with the SRDemo schema.

I don't see how this could be related to Ubuntu or linux, but it happened on two different computers, one running Dapper, and another running Feisty, and since nobody else seems to have this problem...

---

