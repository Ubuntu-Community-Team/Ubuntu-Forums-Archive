---
title: "A Good JDBC Driver"
date: 2007-09-21
forum: Programming Talk
---

### Post by Black Mage on 2007-09-21
Whats a good JDBC driver that works well with Java, Ubuntu and Microsoft Access?

---

### Post by blastus on 2007-09-25
There is no native JDBC driver for Microsoft Access. To use JDBC with Access, you to use the JDBC-ODBC bridge driver that is a part of JDBC. There isn't any way to use JDBC with an Access database on Ubuntu as Access requires Windows. There might be a way to do it with Wine but I wouldn't bother with it. 

If you want a lightweight database that will work on any Java-platform, I would recommend HSQL.

---

