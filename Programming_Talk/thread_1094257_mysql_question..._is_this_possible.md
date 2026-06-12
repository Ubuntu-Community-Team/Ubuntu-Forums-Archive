---
title: "mysql question... is this possible?"
date: 2009-03-12
forum: Programming Talk
---

### Post by lapubell on 2009-03-12
hello wonderful world or geniuses.

after reading my book and googleing for about an hour, i have decided to ask while i continue my search.  please let me know if what i want to do is possible, as i'm not sure if it is...

so here is some fake data that i can use as an example:

```

mysql> select * from strings;
+----+--------+
| id | string |
+----+--------+
|  1 | puppy  | 
|  2 | kitty  | 
|  3 | happy  | 
|  4 | sad    | 
|  5 | chubby | 
|  6 | bad    | 
|  7 | lalala | 
+----+--------+
7 rows in set (0.00 sec)

```

is there a select syntax that will return all values from the string column, in one row?  such as this?

```

mysql> select SOME SORT OF MAGIC HERE;
+-----------------------------------------+
| string                                  |
+-----------------------------------------+
| puppy,kitty,happy,sad,chubby,bad,lalala | 
+----+--------+
1 row in set (0.00 sec)

```

does such a thing exist?

---

### Post by BackwardsDown on 2009-03-12
Why would you want them in 1 row? With any programming language you can create you own layout.

You ask in SQL wich entry's you want to see, and mysql gives them to you. Don't use SQL for stuff like formatting.

---

### Post by shadow_code on 2009-03-12
I think this is what you're looking for:

[http://dev.mysql.com/doc/refman/5.0/en/group-by-functions.html#function_group-concat](http://dev.mysql.com/doc/refman/5.0/en/group-by-functions.html#function_group-concat)

e.g.

```
SELECT GROUP_CONCAT(string)
FROM strings
GROUP BY *;
```

I'm not sure if the "group by *" will work. You might need to have a common field or a "match all" wildcard or something.

Though I agree with above, that it's probably best to reserve SQL for fetching and a programming language for manipulating (if possible).

---

### Post by lapubell on 2009-03-12
sorry but i have to disagree.  i'm trying to return a formatted list so that i can use my query in a bunch of different programs, and with the one magic query, i won't have to rewrite the formatting functions in different languages.

If this is bad, then i bought a bad book.  I think it sounds like an ok idea to me, but if it is really bad news to have my data returned formatted, then i would like to know.

Anyway, I found the mysql function GROUP_CONCAT and it's doing what i want.  however i'm getting caught up now on my real query which contains a join.  Any good docs or tutorials on using this function?  or any other ideas?

---

### Post by lapubell on 2009-03-12
thanks for all the help everyone.  I think that we figured it out!

@shadow_clone, thanks it was the group by that we were messing up...

---

### Post by shadow_code on 2009-03-12
> **lapubell said:**
> i'm trying to return a formatted list so that i can use my query in a bunch of different programs, and with the one magic query, i won't have to rewrite the formatting functions in different languages.

Sounds like a good reason to me ;)

---

