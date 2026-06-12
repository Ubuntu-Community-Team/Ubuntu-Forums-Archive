---
title: "SQL query for column cumulations"
date: 2010-03-22
forum: Programming Talk
---

### Post by jacksmash on 2010-03-22
Ok, so here's what I'm trying to do:

I have an initial table, like so:

```

name | date | candies_eaten
-----------------------
Bob  |   1   |    3
Bob  |   2   |    4
Bob  |   7   |    1
James |  1   |    1
James |  4   |    2

```

(Sorry if that's messy!)

Now, I simply want to cumulate the candies_eaten column for each individual. The above table would translate to:

```

name | date | candies_eaten
-----------------------
Bob  |   1   |    3
Bob  |   2   |    7
Bob  |   7   |    8
James |  1   |    1
James |  4   |    3

```

Note that the cumulation starts over at each individual.

So, I was thinking of using a query something like this:

```

SET @total:=0
SELECT name,date,(@total:=@total+(candies_eaten)) FROM table_name (GROUP BY ??)

```

But I need to reset @total to zero each time we get to a new person in the table.

Thanks for any insights.

---

### Post by thebigob on 2010-03-22
```
select name,sum(candies_eaten) from table_name group by name
```

---

### Post by CptPicard on 2010-03-22
AFAIK straight SQL can't do running totals *efficiently*, you need external code for that.

There is a way of self-joining the table so that each row gets associated with the *previous* rows, and then you can do the summing over that to get the running subtotal for each combination of name and day, but that is very inefficient on large datasets as it produces a quadratic result for the aggregate function... not sure if any database's query optimizer is bright enough to run a linear-time tally.

Namely... something like this kind of a join you then sum over:

```

select ... from tablename as x, tablename as y where x.name=y.name and y.date <= x.date ...

```

---

