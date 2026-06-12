---
title: "Python MySQLdb Question"
date: 2007-06-21
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2007-06-21
Hi

I have written a little test program that basically sends a query to a mysql db on another machine on my work network,(windows based), the database server is a ubuntu machine and the client side is dual boot win xp /ubuntu.

My problem is that if I run the program under ubuntu it connects fine and returns the result of the query. If I run it when booted into win xp with python 2.5 and the MySQLdb modules installed, it says error 2003 ( which is unable to connect to that machine), and doesnt return the results.

As the code runs fine with the ubuntu version of python I know it cant be the code malfunctioning. however, could it be that there are extra networking type things I need to do when running under the xp platform that you dont when under ubuntu?

Mike

---

### Post by Mickeysofine1972 on 2007-06-21
ok forget it i fixed it!

Stupid windows fire wall waqs blocking port 3306! Duh!

Mike

---

