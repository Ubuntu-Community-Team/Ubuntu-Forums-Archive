---
title: "MySQL: How do you use INT correctly?"
date: 2007-06-04
forum: Programming Talk
---

### Post by jingo811 on 2007-06-04
I'm doing my tables for my database.  Now I'm about to assign data types for each field.
I've learnt to do things like this regarding numbers from my teacher:

```
CREATE TABLE Clothes (
  article_id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT, # PK
...
...
  PRIMARY KEY (article_id)
);

```

Now I want to adjust the situations for certain fields like for my Order_id field.  I want to be able to handle numbers beyond the 1 Million mark.
Acording to this google search:
[http://dev.mysql.com/doc/refman/4.1/en/numeric-type-overview.html](http://dev.mysql.com/doc/refman/4.1/en/numeric-type-overview.html)

I can achieve that with this:
> INT[(M)] [UNSIGNED] [ZEROFILL]

A normal-size integer. The signed range is -2147483648 to 2147483647. The unsigned range is 0 to 4294967295. 

But I don't understand how to use the (M) part in:
**INT[(M)] UNSIGNED**

Can I just leave the (M) empty?  Or should I put in the number 4.294.967.295?

---

### Post by bvanaerde on 2007-06-04
If I'm not mistaken, the (M) part is the amount of characters the value can be.
When you don't fill it in, it is automatically 11 (being the maximum).

---

### Post by LaRoza on 2007-06-04
You can use a different data type for higher numbers, like MEDIUMINT and BIGINT. Making an integer data type unsigned increases the range.

---

### Post by jingo811 on 2007-06-04
Ooh I missed the BIGINT part from doing that google search.  Now that's some BIGARSSE number :D
hmmm...so if today I use MEDIUMINT and the posts grows beyond it's parameter is it just a simple matter of changing the relevant line in the script to INT or BIGINT to adapt to the changing situation?

Or will doing so later on when you have some millions of relations of posts and fields make the whole database go loco?

---

### Post by jingo811 on 2007-06-04
Also another thing I wonder about.
```

CREATE TABLE Gender (
  gender_id **TINYINT** UNSIGNED NOT NULL AUTO_INCREMENT, # PK ,  Only need 3 ids what to do???
  gender VARCHAR(6) NOT NULL,
  PRIMARY KEY (gender_id)
);
```

TINYINT is the smallest number data type for AUTO_INCREMENT I know of.  How do I constrain its max capacity of 255 to only 3?
Do you think it's neccessary for me to do so or will TINYINT be good enough without eating too much processing time?

---

### Post by LaRoza on 2007-06-04
If you only have a few possible values, like a gender, using an ENUM data type would be better.

---

### Post by AdamG on 2007-06-05
unsigned Tinyint(2) will limit you to three values:0, 1,2. 

But the performance benefit will be marginal. Tell the database what you (concptually) want, and let the database handle optimization. It's certainly possible to do better than the database, but I'd leave that to people with DBA degrees :)

---

### Post by jingo811 on 2007-06-05
tnx for the tip!

---

