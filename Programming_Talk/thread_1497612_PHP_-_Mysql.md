---
title: "PHP - Mysql"
date: 2010-05-30
forum: Programming Talk
---

### Post by rp3 on 2010-05-30
```
$query = "SELECT * FROM `tsk_dt` where tsk_code IN
   (SELECT * FROM 'tsk_dt' where tsk_list LIKE '%$search_inp%')";
```

Anyone see the issue with this, mysql and PHP are kind of new to me, but if I do either select it works fine, but when I try to 'embed' it doesn't work... 

Thanks,

---

### Post by LoneWolfJack on 2010-06-01
```

$query = "SELECT * FROM `tsk_dt` where tsk_code IN
   (SELECT DISTINCT tsk_code FROM 'tsk_dt' where tsk_list LIKE '%$search_inp%')";

```

NOTE:
#1 don't use "SELECT ... IN(SELECT ...) for performance reasons
#2 don't use "LIKE" for performance reasons
#3 don't use "LIKE '%" for performance reasons
#4 properly escape $search_inp

---

### Post by rp3 on 2010-06-03
> **LoneWolfJack said:**
> ```

$query = "SELECT * FROM `tsk_dt` where tsk_code IN
   (SELECT DISTINCT tsk_code FROM 'tsk_dt' where tsk_list LIKE '%$search_inp%')";

```

NOTE:
#1 don't use "SELECT ... IN(SELECT ...) for performance reasons
#2 don't use "LIKE" for performance reasons
#3 don't use "LIKE '%" for performance reasons
#4 properly escape $search_inp

Performance isn't an issue at this time, getting it to work is.  

I try each select statement separately and they work fine, but they don't work with I do the IN (SELECT... part?  

Could this be a database setup issue?  I just primary used defaults for this testing?

And for #4 it works fine, this isn't why its not working, can you give me an example?

Hmmmmm

Thanks for the reply though....I will keep fidilng with it...

---

### Post by januzi on 2010-06-03
If You insist:  
$query = "SELECT * FROM `tsk_dt` where tsk_code IN
(SELECT tsk_code FROM 'tsk_dt' where tsk_list LIKE '%$search_inp%')";

---

### Post by new_tolinux on 2010-06-03
> **LoneWolfJack said:**
> [CODE]
#2 don't use "LIKE" for performance reasons
#3 don't use "LIKE '%" for performance reasons

Would you mind pointing me/us to a different type of query which has the same functionality but is more performance-friendly?
Afaik LIKE '%".$searchstring."%' is the only way of searching text that matches part of a field's content.

ps. I like to separate PHP-strings from text inside a query, therefore I use '%".$searchstring."%' instead of '%$searchstring%'.

---

### Post by LoneWolfJack on 2010-06-03
> I try each select statement separately and they work fine, but they don't work with I do the IN (SELECT... part? 

The query should work. What's the error message mysql returns?

> Would you mind pointing me/us to a different type of query which has the same functionality but is more performance-friendly?
Afaik LIKE '%".$searchstring."%' is the only way of searching text that matches part of a field's content.

If you have to rely on LIKE, there's probably something wrong with your table layout. LIKE is absolutely useless when you have to evaluate many rows, Use MATCH() instead. If you really need partial matches, you'll have to create an index table yourself.

---

