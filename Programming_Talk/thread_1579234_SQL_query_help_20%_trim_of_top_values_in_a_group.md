---
title: "SQL query help: 20% trim of top values in a group"
date: 2010-09-21
forum: Programming Talk
---

### Post by bkann on 2010-09-21
Hi -

I've clearly reached the edge of my SQL knowledge.  I would like to write a query that excludes the top 20% of records from a group of values.

For example, in the following table, there are 10 records in the first and 5 in the second group.  I would like to generate a result set that includes everything in the table below except for values (1,9),(1,10),(2,904).

Can this be done?  Can anyone help me with this?  Thanks very much for any help you can provide!

```

Group  Value
1      1
1      2
1      3
1      4
1      5
1      6
1      7
1      8
1      9
1      10
2      3
2      6
2      15
2      145
2      904
```

---

### Post by r-senior on 2010-09-21
In pure SQL, you'd probably use a [correlated subquery](http://www.craigsmullins.com/dbu_0502.htm) for this type of thing.

For other examples of basically the same problem:

[http://www.evolt.org/node/131]("http://www.evolt.org/node/131")
[http://searchoracle.techtarget.com/answer/How-to-find-the-first-5-highest-salaried-employees-in-each-department]("http://searchoracle.techtarget.com/answer/How-to-find-the-first-5-highest-salaried-employees-in-each-department")

The first step is to write the query that identifies the 20%, then use that as the correlated subquery to return the rows you need.

---

### Post by bkann on 2010-09-21
Thanks very much for the info, r-senior.  I agree that this may take me down the path of correlated subqueries.

As I read through your links, however, they seem to work with static or known value divisions, like 'Top 10' terms.  I suspect my situation is a little more complicated in that each group will have a different number of records within it, and I want to look at the 20% of records that constitute the bottom of that group.

Thanks again for the links and I'll try to adapt them to my situation.  In the meantime, I'm open to ideas if anyone has any.

Thanks!

---

