---
title: "SQL help for a beginning"
date: 2007-09-16
forum: Programming Talk
---

### Post by DouglasAWh on 2007-09-16
Here's the English query:
"A customer wants to travel from Madison to New York with no more than two changes of flight.  List the choice of departure times from Madison if the customer wants to arrive in New York by 6pm."

I'd post the whole table, but the window isn't large enough to pull from terminal and paste here.

Here's the schema (primary keys are always first):
FLIGHTS (flno, origin, destination, distance, departs, arrives, price)
AIRCRAFT (aid, aname, cruisingrange)
CERTIFIED (eid, aid)
EMPLOYEES (eid, ename, salary)

Please don't post the complete answer, since I'm working on this for class.  I'm just stuck and need a new idea.


I'm thinking something similar to 
```
SELECT departs 
FROM flights 
WHERE departs <  arrives < ANY 
     (SELECT departs 
      FROM flights 
      WHERE arrives<'2005-04-12 18:00:00' AND destination="New York");
```

but that particular query doesn't work.  Even if I did get this working, I feel like this would force the flight to have one stop.  Does anyone agree with that?  I feel like I need an if-then statement, but I'm not sure how to do that in SQL.

Thanks!

---

### Post by paulvas on 2007-09-16
I would try something like this for one-stop flight. You can join another flight table for 2-stop flight.

```

SELECT f1.flno, f2.flno 
FROM flights f1, flights f2 
WHERE f1.destination=f2.origin
  and f1.origin="Madison"
  and f2.destination="New York"
  and f2.departs > f1.arrives
  and f2.arrives<'2005-04-12 18:00:00'

```

For non-stop flight:
```

SELECT f1.flno
FROM flights f1
WHERE 
  f1.origin="Madison"
  and f1.destination="New York"
  and f1.arrives<'2005-04-12 18:00:00'

```

You can union those queries into one.

---

### Post by DouglasAWh on 2007-09-17
very helpful!  Thank you!

I'm going to be working a while longer on these two more and then I might post again.

---

### Post by rock freak on 2007-09-18
Hey im justing mastering joins at the moment and stumbled accross this site which is bloody usful :)

Know idea if it will be any use to you but thought I'd post it regardless :)

[The Linky]("http://www.keithjbrown.co.uk/vworks/mysql/mysql_p1.php")

---

