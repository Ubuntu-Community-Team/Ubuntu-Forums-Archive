---
title: "MySQL and EXCEPT"
date: 2007-09-22
forum: Programming Talk
---

### Post by DouglasAWh on 2007-09-22
I found [http://bugs.mysql.com/bug.php?id=1309](http://bugs.mysql.com/bug.php?id=1309) from 2005, but does MySQL still not support EXCEPT?  This would be very help to me at the time being, if it did.  It looks like we are using 4.0.20-standard and I don't think I have the ability to upgrade this, so maybe it's just the version I am using and it has been added to newer MySQL implementations.

Ok, I've done some more research and 5.0.43 is the latest version of MySQL.  I've got access to 5.0.22 now on another box.  I still can't seem to get this EXCEPT stuff down.  I did find [http://dev.mysql.com/doc/maxdb/en/ed/1f2a40ce93185de10000000a1550b0/content.htm](http://dev.mysql.com/doc/maxdb/en/ed/1f2a40ce93185de10000000a1550b0/content.htm) which makes it sound like it should work.

Alright, here's some code for you
```


mysql> 
SELECT emp.salary 
FROM emp 

EXCEPT 

SELECT E.salary 
FROM emp E, (SELECT D.managerid FROM dept D) AS M 
WHERE M.managerid=E.eid;


```

Error:
```

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'SELECT E.salary FROM emp E, (SELECT D.managerid FROM dept D) AS M WHERE M.manage' at line 1

```

---

### Post by altonbr on 2009-11-12
Looks like it's still not supported in 5.0...
 
```
SELECT S.sname
FROM Sailors S
WHERE NOT EXISTS ((SELECT B.bid FROM Boats B) EXCEPT (SELECT R.bid FROM Reserves R WHERE R.sid=S.sid));
```
 
```
[FONT=Courier New][COLOR=red]#1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'EXCEPT (SELECT R.bid FROM Reserves R WHERE R.sid=S.sid))[/COLOR][/FONT]
[FONT=Courier New][COLOR=red]LIMIT 0, 30' at line 3[/COLOR] [/FONT]
```

---

