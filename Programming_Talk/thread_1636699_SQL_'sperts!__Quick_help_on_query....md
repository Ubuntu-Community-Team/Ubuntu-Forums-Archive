---
title: "SQL 'sperts!  Quick help on query..."
date: 2010-12-03
forum: Programming Talk
---

### Post by era86 on 2010-12-03
Hey all!  I am currently trying to get some data using the following query:
```

SELECT PZ.ID, PZ.CUST, (SELECT TP.NAME FROM TOPPING TP WHERE TP.TYPE = 'meat' AND TP.ID = PZ.ID) AS TOP FROM PIZZA PZ

```
If my tables look like this:
```

PIZZA:
[ID: 0, CUST: 'dave']
[ID: 1, CUST: 'bob']
[ID: 2, CUST: 'tracy']

TOPPING:
[ID: 0, NAME: 'pep', TYPE: 'meat']
[ID: 3, NAME: 'mushroom', TYPE: 'veggie']
[ID: 1, NAME: 'mozzarella', TYPE: 'cheese']
[ID: 1, NAME: 'sausage', TYPE: 'meat']
[ID: 0, NAME: 'mozzarella', TYPE: 'cheese']

```
the above query would return me the following information:
```

[ID: 0, CUST: 'dave', TOP: 'pep']
[ID: 1, CUST: 'bob', TOP: 'sausage']
[ID: 2, CUST: 'tracy', TOP: '']

```
Now here is my question!  I want to be able to search over the results of this query by possibly using a WHERE clause at the end that would do something like this:
```

SELECT PZ.ID, PZ.CUST, (SELECT TP.NAME FROM TOPPING TP WHERE TP.TYPE = 'meat' AND TP.ID = PZ.ID) AS TOP FROM PIZZA PZ **WHERE TOP LIKE '%sau%'**

```
To get only Bob's pizza:
```

[ID: 1, CUST: 'bob', TOP: 'sausage']

```
Is this possible?  Am I missing an alias somewhere possibly?  Maybe nest yet another SELECT around the query and do the WHERE there?  Any thoughts would be much appreciated!  Thank you so much!

---

### Post by Paul41 on 2010-12-03
This would work on ORACLE. I'm not sure which db platform you are using so it may or may not work for you.

```
SELECT PZ.ID, PZ.CUST, TP.NAME
FROM PIZZA PZ,
    (SELECT NAME FROM TOPPING WHERE TYPE = 'meat') TP
WHERE PZ.ID = TP.ID
    AND TP.TOP LIKE '%sau%'
```

---

### Post by era86 on 2010-12-03
> **Paul41 said:**
> This would work on ORACLE. I'm not sure which db platform you are using so it may or may not work for you.

```
SELECT PZ.ID, PZ.CUST, TP.NAME
FROM PIZZA PZ,
    (SELECT NAME FROM TOPPING WHERE TYPE = 'meat') TP
WHERE PZ.ID = TP.ID
    AND TP.TOP LIKE '%sau%'
```

Hey thanks for the reply.  I see what you did and I'm sure this will work in my context, but I'm trying to avoid moving the subselect into the join portion of it.  I will be doing up to 4 joins on the same table, each with a different TYPE specified.  I am seeing performance issues with that.  Is it possible at all to avoid?

---

### Post by Paul41 on 2010-12-03
The only way I can think of to keep it like you have it is like this, but it puts you running the subquery twice, which I would think would be more of a performance hit.

```
SELECT PZ.ID, PZ.CUST, (SELECT TP.NAME FROM TOPPING TP WHERE TP.TYPE = 'meat' AND TP.ID = PZ.ID) AS TOP FROM PIZZA PZ WHERE (SELECT TP.NAME FROM TOPPING TP WHERE TP.TYPE = 'meat' AND TP.ID = PZ.ID) LIKE '%sau%'
```

---

### Post by lucasart on 2010-12-03
> **era86 said:**
> Hey thanks for the reply.  I see what you did and I'm sure this will work in my context, but I'm trying to avoid moving the subselect into the join portion of it.  I will be doing up to 4 joins on the same table, each with a different TYPE specified.  I am seeing performance issues with that.  Is it possible at all to avoid?

Paul41's solution looks good. If you ahve performance issue, did you try to rewrite it using an INNER JOIN instead of doing the jointure in the WHERE ? That's typically the right way of coding in SQL :-)

---

### Post by era86 on 2010-12-03
> **lucasart said:**
> Paul41's solution looks good. If you ahve performance issue, did you try to rewrite it using an INNER JOIN instead of doing the jointure in the WHERE ? That's typically the right way of coding in SQL :-)

Hey I actually needed to do a LEFT OUTER JOIN for my needs, but I get your point. ;)

> **Paul41 said:**
> The only way I can think of to keep it like you have it is like this, but it puts you running the subquery twice, which I would think would be more of a performance hit.

```
SELECT PZ.ID, PZ.CUST, (SELECT TP.NAME FROM TOPPING TP WHERE TP.TYPE = 'meat' AND TP.ID = PZ.ID) AS TOP FROM PIZZA PZ WHERE (SELECT TP.NAME FROM TOPPING TP WHERE TP.TYPE = 'meat' AND TP.ID = PZ.ID) LIKE '%sau%'
```

Hey I actually ended up using your first suggestion.  My performance hit was coming from doing a SELECT * on my subselect in the join.  By just grabbing the fields I needed from the subtable (TOPPING in my example), I was able to greatly reduce the time on the query.

And now, my problem is solved!

Thanks to both of ya!:popcorn:

---

