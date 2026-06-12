---
title: "Three column from MySQL to PHP array?"
date: 2018-08-06
forum: Programming Talk
---

### Post by cazz on 2018-08-06
Hi
I have a SQL that get some information from three column in a MySQL database


How do I get them to a array?


I think array is the best idea to easy access the information to write on the page or compare info
Or is that some better way??

---

### Post by spjackson on 2018-08-06
What have you tried? Have you got a connection working? This should help: [http://php.net/manual/en/pdo.query.php](http://php.net/manual/en/pdo.query.php)

---

### Post by cazz on 2018-08-06
That I have done is this and got it to work

```
select t1.state, t1.entity_id, t1.last_updated 
from states as t1 
inner join ( 
   select entity_id, max(state_id) as last_id 
   from states 
   group by entity_id 
) as t2 on t1.entity_id = t2.entity_id and t1.state_id = t2.last_id
```

---

