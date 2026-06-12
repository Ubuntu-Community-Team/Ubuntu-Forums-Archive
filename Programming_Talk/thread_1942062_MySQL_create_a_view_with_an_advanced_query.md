---
title: "MySQL create a view with an advanced query"
date: 2012-03-16
forum: Programming Talk
---

### Post by CyberAngel on 2012-03-16
Hello,

I have a MySQL database with the following table holding memory data and timestamps. Pretty simple data like memory used and memory total available in the system.
Now I would like to create a view after making some simple calculations in this data.


```
date                     |mem_used    |mem_total
2012-03-16 23:29:05      |467         |1024
2012-03-16 23:30:05      |432         |1024
2012-03-16 23:31:05      |490         |1024
2012-03-16 23:33:05      |501         |1024
2012-03-16 23:35:05      |396         |1024
2012-03-16 23:39:05      |404         |1536
2012-03-16 23:43:05      |801         |1536
```

The view should look like the following one.

```
date                     |mem_used    |mem_total    |mem_5_min_avg    |mem_rate_usage
2012-03-16 23:29:05      |467         |1024         |473              |0.46191406
2012-03-16 23:30:05      |432         |1024         |455              |0.44433594
2012-03-16 23:31:05      |490         |1024         |463              |0.45214844
2012-03-16 23:33:05      |501         |1024         |449              |0.43847656
2012-03-16 23:35:05      |396         |1024         |396              |0.38671875
2012-03-16 23:39:05      |404         |1536         |603              |0.39257813
2012-03-16 23:43:05      |801         |1536         |801              |0.52148438
```

Requirements:
The first 3 columns are the same, but the column mem_5_min_avg should contain the average used memory for the following 5 minutes, given that the mem_total is the same (mem_total is changing).
So the following rows for mem_5_min_avg should be calculated as follows (the numbers has to be rounded to ceiling meaning that 4.1=5):

1st row of the mem_5_min_avg column (467+432+490+501)/4 = 1890/4 = 472.5 = 473    <- We sum up 4 rows here because 2012-03-16 23:29:05 plus 5 minutes 2012-03-16 23:34:05
2nd row of the mem_5_min_avg column (432+490+501+396)/4 = 1819/4 = 454.75 = 455
3rd row of the mem_5_min_avg column (490+501+396)/3 = 1387/3 = 462.33 = 463
4th row of the mem_5_min_avg column (501+396)/2 = 897/2 = 448.5 = 449
5th row of the mem_5_min_avg column 396    <- We do not sum any rows here because even if the next measurement is within 5 minutes, the mem_total has changed.
6th row of the mem_5_min_avg column (404+801)/2 = 1205/2 = 602.5 = 603
7th row of the mem_5_min_avg column 801

After the mem_5_min_avg is calculated, I need mem_rate_usage column which shows a simple rate of how much memory is used given in percentage.

mem_rate_usage = mem_5_min_avg / mem_total

For example the 3rd row of mem_rate_usage should be calculated like 463/1024=0.45214844, while the last column should be calculated like this 801/1536=0.52148438

Any clue on how to do that?

Thanks!

---

### Post by TeoBigusGeekus on 2012-03-17
Table test:
```
date                     |mem_used    |mem_total
2012-03-16 23:29:05      |467         |1024
2012-03-16 23:30:05      |432         |1024
2012-03-16 23:31:05      |490         |1024
2012-03-16 23:33:05      |501         |1024
2012-03-16 23:35:05      |396         |1024
2012-03-16 23:39:05      |404         |1536
2012-03-16 23:43:05      |801         |1536
```
date: timestamp
mem_used: int
mem_total: int

Then

```
SELECT date,mem_used,mem_total,(SELECT ceiling(avg( mem_used)) FROM test AS test2 WHERE TIMESTAMPDIFF(MINUTE,test1.date,test2.date) <=5 AND test2.date >= test1.date AND test1.mem_total=test2.mem_total) AS mem_5_min_avg,(SELECT ceiling(avg(mem_used))/mem_total FROM test AS test3
WHERE TIMESTAMPDIFF(MINUTE,test1.date,test3.date) <=5 AND test3.date >= test1.date AND test1.mem_total = test3.mem_total) AS mem_rate_usage FROM test AS test1

```

If you've used datetime instead of timestamp, just change timestampdiff with timediff.

EDIT: Hi patrioti.

---

### Post by CyberAngel on 2012-03-17
Thank you very much (&#917;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974; &#960;&#959;&#955;&#973; &#947;&#953;&#945;&#964;&#943; &#946;&#955;&#941;&#960;&#969; &#917;&#955;&#955;&#940;&#948;&#945; :))

It works perfectly, but it is sooooooooooooooo slow for my table that it contains more than 100000 rows :/

If I limit the query to 30 rows it takes around 7.5 seconds and more than 20 seconds for 100 rows... I don't even want to think how much it needs for 100.000 rows.

I guess I have to come up with a different external solution..

---

### Post by TeoBigusGeekus on 2012-03-17
Do you have an index in your table? That could speed things up a bit...

7.5 secs for 30 rows is abnormal by the way...

---

### Post by CyberAngel on 2012-03-17
> **TeoBigusGeekus said:**
> Do you have an index in your table? That could speed things up a bit...

7.5 secs for 30 rows is abnormal by the way...

hmmmmm

I am running the query directly on a created VIEW and as I read here: [http://dev.mysql.com/doc/refman/5.0/en/view-restrictions.html](http://dev.mysql.com/doc/refman/5.0/en/view-restrictions.html)
View processing is not optimized! It is not possible to create an index on a view.

I will try to run in on my default table and report back about any speedups.

---

### Post by CyberAngel on 2012-03-17
> **CyberAngel said:**
> hmmmmm

I am running the query directly on a created VIEW and as I read here: [http://dev.mysql.com/doc/refman/5.0/en/view-restrictions.html](http://dev.mysql.com/doc/refman/5.0/en/view-restrictions.html)
View processing is not optimized! It is not possible to create an index on a view.

I will try to run in on my default table and report back about any speedups.

I ran the same query on my main table that it is indexed and still very slow.. This is the result for 100 lines:

```
Showing rows 0 - 29 ( 100 total, Query took 28.3982 sec)
```

If I re-run the same query then the result is instant, but that's I guess because of the query cache.

---

### Post by CyberAngel on 2012-03-17
I've got a twice as fast query but still very slow.



```
SELECT  `date` ,  `mem_used` ,  `mem_total` , `mem_5_min_avg` , (`mem_5_min_avg` / `mem_total`) AS mem_usage_rate
FROM (
   SELECT *, (
      SELECT CEILING( AVG( mem_used ) )
      FROM `data` AS t2
      WHERE TIMESTAMPDIFF(
      MINUTE , t1.date, t2.date ) <=5
      AND t2.date >= t1.date
      AND t1.mem_total = t2.mem_total
   ) AS mem_5_min_avg
   FROM `data` AS t1 LIMIT 0 , 100
) AS t1
```

```
Showing rows 0 - 29 ( 100 total, Query took 14.1438 sec)
```

---

### Post by TeoBigusGeekus on 2012-03-17
Could you send me an sql file of your db - if you don't mind - to test the times myself?

---

### Post by CyberAngel on 2012-03-17
> **TeoBigusGeekus said:**
> Could you send me an sql file of your db - if you don't mind - to test the times myself?

No prob! Check your private messages :)

---

### Post by TeoBigusGeekus on 2012-03-17
Ouch!!! The times on my rusty P4 were even worse than yours...
One last thing I'd try is to create an index for these 3 columns
```
CREATE INDEX test_index ON data(date,mem_used,mem_total);
```
and then query again...

---

### Post by CyberAngel on 2012-03-17
> **TeoBigusGeekus said:**
> Ouch!!! The times on my rusty P4 were even worse than yours...
One last thing I'd try is to create an index for these 3 columns
```
CREATE INDEX test_index ON data(date,mem_used,mem_total);
```
and then query again...

Tried it but it's hopeless. No improvement :(

Thanks a lot for your time!

Cheers

---

### Post by TeoBigusGeekus on 2012-03-17
You're welcome (for nothing as it seems).
Another idea: you could try creating a different table with only the 3 fields you want queried. 
Tell me if it's feasible and, if it is, whether it works.

---

### Post by CyberAngel on 2012-03-17
> **TeoBigusGeekus said:**
> You're welcome (for nothing as it seems).
Another idea: you could try creating a different table with only the 3 fields you want queried. 
Tell me if it's feasible and, if it is, whether it works.

I didn't even try it.. Looks hopeless. I made a Perl script and converted all of the data much much faster (still the MySQL queries was the bottleneck in the procedure)

I also made the same question to the mysql forums and I got this answer

[http://forums.mysql.com/read.php?10,520559,520565#msg-520565](http://forums.mysql.com/read.php?10,520559,520565#msg-520565)

> Posted by: Peter Brawley ()
Date: March 17, 2012 07:42PM

MySQL Views do not optimise well. 

Even without such problems, there's no way calculating all those moving averages is going to be fast. Consider a Trigger that calculates the averages that any inserted or updated value participates in and writes them to an intermediate_results table which you can then query for your report.

Do you have a clue on how to create a trigger that it will update an intermediate table?

I guess the logic should be something like this:

Got New Data in my data table? Check the date from the newly added line and go back 5 minutes and update the created averages in the intermediate table.

Tired for today.. Going to sleep and I'll look at it again tomorrow.

---

