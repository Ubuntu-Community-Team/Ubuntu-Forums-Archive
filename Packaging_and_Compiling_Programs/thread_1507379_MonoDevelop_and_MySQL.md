---
title: "MonoDevelop and MySQL"
date: 2010-06-11
forum: Packaging and Compiling Programs
---

### Post by IllegalCharacter on 2010-06-11
I'm trying to get a basic MySQL program to compile in MonoDevelop, however I'm running into some issues. I correctly installed the MySQL connector as described here: [http://dev.mysql.com/doc/refman/5.5/en/connector-net-installation-unix.html](http://dev.mysql.com/doc/refman/5.5/en/connector-net-installation-unix.html)

When I check the references for the project the MySql.Data one is red and I get "Assembly not available for Mono / .NET 3.5 (in Mono 2.4.4)"

Does anybody know how to fix this?

---

### Post by IllegalCharacter on 2010-06-11
Oops never mind, I figured it out. What you have to do is remove the reference to MySQL and then load in the MySql.Data.dll file manually.

---

