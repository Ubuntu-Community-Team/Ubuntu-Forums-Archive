---
title: "MySQL QUERY Help Needed!!"
date: 2010-12-02
forum: Programming Talk
---

### Post by ivikas on 2010-12-02
Hello all,

            i have a mysql table with following data

```

  id   Date                     Total
  1    2009-11-01 11:34:23      30
  2    2009-11-07 00:00:00      20
  3    2009-11-18 12:10:32      10
  4    2010-02-04 11:35:55      20

```

Now i need a result assuming   2009-11-01 11:34:23 as MIN date an out put like this

```

  WeeK           WeekTotal
  07  Nov 2009   50 ---------->(Nov 1 To Nov 7,so    30+20=50
  21  Nov 2009   10 ---------->(Nov 18 falls between week start date 
                                14  Nov 2009 and Week end date 21 Nov 
                                2009, so Nov 21)
  07 Feb 2010   20

```

Can any one figure out to do this either with sql query itself or with both mysql query + php.

An idea will be highly appreciated.

Thanks in advance

---

### Post by DaithiF on 2010-12-02
this won't win any prizes for clarity, but...

```
select from_days(ceiling(to_days(dt)/7)*7) as 'week_end',sum(num) from scratch
group by week_end;

```

```

 week_end     sum(num)    
 -----------  ----------- 
 07/11/2009   50          
 21/11/2009   10          
 06/02/2010   20          

```

---

### Post by ivikas on 2010-12-02
Thanks alot

---

### Post by Some Penguin on 2010-12-02
Have you actually bothered looking at the MySQL manual?

---

### Post by ivikas on 2010-12-02
Hi Some Penguin,
                Iam new to MySQL.Can you suggest a website from which i can find and learn some some pratical queries.

Thanks in advance

---

### Post by lykeion on 2010-12-02
MySQL Reference Manual is the obvious place to get info:
[http://dev.mysql.com/doc/refman/5.1/en/](http://dev.mysql.com/doc/refman/5.1/en/)

---

