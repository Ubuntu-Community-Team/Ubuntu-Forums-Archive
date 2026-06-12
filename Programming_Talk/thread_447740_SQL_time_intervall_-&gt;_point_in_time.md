---
title: "SQL: time intervall -&gt; point in time"
date: 2007-05-18
forum: Programming Talk
---

### Post by rustikus on 2007-05-18
Hi,

i have the following problem.
I have a table with informations to several reservations. The table has an id for the reservation number, a start time and an end time. It looks like the following:

```


id           bookId               start                          end

1                1           2007-05-01 10:00     2007-05-01 11:44
2                6           2007-05-01 09:00     2007-05-03 12:44
3                2           2007-05-02 16:00     2007-05-03 11:44
4                1           2007-05-03 17:00     2007-05-05 13:44


```

I am interested in the information which book was reserved during a specific timespan (i.e. 10:00-11:00  of a specific day, but in a view for all days and hours). Is there a simple way to extract this information from this table?

Thanks,
rustikus

---

### Post by steve.horsley on 2007-05-18
How about this:
If your period you are interested in is from times a to b, then 
SELECT * FROM reservations WHERE a <= end AND b >= start;

---

### Post by rustikus on 2007-05-19
Hi,

but then i have to specify the timespan before.
I think it should be possible with a view containing the data for every hour of a day. The result should be something like:

```

id           bookId               start                          end                         interval/hours

2                6           2007-05-01 09:00     2007-05-03 12:44   2007-05-01 09:00
1                1           2007-05-01 10:00     2007-05-01 11:44   2007-05-01 10:00
2                6           2007-05-01 09:00     2007-05-03 12:44   2007-05-01 10:00
1                1           2007-05-01 10:00     2007-05-01 11:44   2007-05-01 11:00
2                6           2007-05-01 09:00     2007-05-03 12:44   2007-05-01 11:00
2                6           2007-05-01 09:00     2007-05-03 12:44   2007-05-01 12:00

```

---

### Post by steve.horsley on 2007-05-19
You've changed your requirement now. I don't understand ths new requirement. Can you explain more clearly?

---

