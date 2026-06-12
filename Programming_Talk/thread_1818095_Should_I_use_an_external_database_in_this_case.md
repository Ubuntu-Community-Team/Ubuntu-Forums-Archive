---
title: "Should I use an external database in this case?"
date: 2011-08-04
forum: Programming Talk
---

### Post by zhaotianwu on 2011-08-04
I'm building a small diary application using Python 2.7. The most important problem here is, should I use a XML database to store all the data or an object oriented database like ZOPE? or just serialize them using Python pickles? I know they both have their pros and cons, like XML is more suitable for interoperability, however this application is basically just a desktop application for one user so I guess interoperability is not a concern in this case. Given this, what would be a sensible path choice to store the data, in the long run and better supports SVG visualization? Thanks.

p.s. I guess relational database should be out in this case as the diary part is likely to be very unstructured.

---

### Post by PaulM1985 on 2011-08-04
Isn't a diary just a series of textual entries associated with given dates?  Surely this could be part of a relational database.

---

### Post by zhaotianwu on 2011-08-04
> **PaulM1985 said:**
> Isn't a diary just a series of textual entries associated with given dates?  Surely this could be part of a relational database.

Hi PaulM1985, thanks for replying. No it really is not just textual, it contains pictures, sound clips. I'm sure relational database does not fit my project at the moment, but I'm really not sure which path of database design is best at doing this kind of task? XML? ZOPE? Json? Here is why I'm looking for some advice from experienced members. Thanks.:)

---

### Post by zhaotianwu on 2011-08-04
Please someone with experience in Python data model design share some thoughts here, thanks!

---

### Post by Tony Flury on 2011-08-05
Thios sort of design question is really language indepedent, although some languages might make it easier to do some stuff natively.

Think about your data model first - and then think about how you implement your storage.

As a guide - describe your data and the relationship - every noun in your description will possibly be a data type, and each verb will be a relationship between data types.

Then think about the volumes - if you large amounts of data and complex relationships - then maybe using relational database (such as sqllite) might be appropriate.

If you have a small amount of data then python lists, dictionaries and using pickle to keep data between execution.

---

### Post by PaulM1985 on 2011-08-05
> **Tony Flury said:**
> Thios sort of design question is really language indepedent, although some languages might make it easier to do some stuff natively.

Think about your data model first - and then think about how you implement your storage.

As a guide - describe your data and the relationship - every noun in your description will possibly be a data type, and each verb will be a relationship between data types.

Then think about the volumes - if you large amounts of data and complex relationships - then maybe using relational database (such as sqllite) might be appropriate.

If you have a small amount of data then python lists, dictionaries and using pickle to keep data between execution.

I agree.

You mentioned in your description of a diary entry that the types things allowed in an entry are flexible, but you must have a definitive set on things that are allowed.  This things would be attributes of an entry.

Paul

---

### Post by zhaotianwu on 2011-08-05
Thanks everyone

---

