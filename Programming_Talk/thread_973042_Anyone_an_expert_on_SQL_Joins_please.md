---
title: "Anyone an expert on SQL Joins please?"
date: 2008-11-06
forum: Programming Talk
---

### Post by bluedalmatian on 2008-11-06
Ive got two tables A & B linked with a join table like this:

----------------                
A                                                            
----------------                
id | field2|                                 
----------------                




----------------                
B                                                   
----------------                
id | field2|                                 
----------------







----------------
A_B
----------------
a_id  |    b_id 
----------------


I want a query which will return all B records, which have an entry in the join table for a particular a_id

Which type of join is the best for this please?

Thanks

---

### Post by Paul41 on 2008-11-06
I'm not sure if I understand what you are trying to do but if I do you need a left outer join and then restrict the values to what you want for a_id in the where clause.

---

### Post by bluedalmatian on 2008-11-06
I want all records from B which have a link to a particular A record

---

### Post by Paul41 on 2008-11-06
Then yes, this will work.

---

### Post by bcarvalho on 2008-11-06
Try this statement and tell us if it worked out for ya:

SQL> SELECT a.id, a.field2, b.id, b.field2
2 FROM A a LEFT OUTER JOIN B b
3 ON a.field2 = b.field2 OR a.id = b.id;

Best regards,
Bruno Carvalho

---

### Post by bluedalmatian on 2008-11-06
Thanks Paul

I tried doing

select * from B left outer join a_b on a_id =12

but it didnt work.  Can you enlighten me as to what I should be typing.

Thanks again

Andrew

---

### Post by bluedalmatian on 2008-11-06
bcarvalho i want to search for only a particular A id (e.g all B's which are assocated with A record number 12

---

### Post by koenn on 2008-11-06
select * from A_B inner join B on A_B.b_id = B.id
where a_id = 42 ;

check for syntax errors, my sql is a bit rusty.

---

### Post by Delever on 2008-11-06
I tried to expand it to make it more clear:

[PHP]
select B.id, B.field // this is what fields from b you want to take
    from
       B
          inner join // this is the way you want to join tables B and A_B
              A_B
          on A_B.b_id = B.id // how to join A_B and B
    where
       A_B.a_id = whatever
[/PHP]

This is if you want to include field from A table too:

[PHP]
select B.id, B.field, A.field // this is what fields from b you want to take
    from
       B
          inner join // this is the way you want to join tables B and A_B
              A_B
                    inner join // join A_B and A
                         A
                    on A.id = A_B.a_id // how to join A_B and A
          on A_B.b_id = B.id // how to join A_B and B
    where
       a.id = whatever
[/PHP]

---

### Post by bluedalmatian on 2008-11-06
thanks koenn that works perfectly.

---

### Post by koenn on 2008-11-06
> **bluedalmatian said:**
> thanks koenn that works perfectly.

cool.
Was it home work ?

---

### Post by bluedalmatian on 2008-11-09
lol no its for this program Im writing.

what about doing something similar in reverse...like this  [http://www.simple.org/sqlexample.png](http://www.simple.org/sqlexample.png)

---

### Post by koenn on 2008-11-09
> **bluedalmatian said:**
> lol no its for this program Im writing.

what about doing something similar in reverse...like this  [http://www.simple.org/sqlexample.png](http://www.simple.org/sqlexample.png)

same as before, except you include table A in the join, and you'd say "where B.fiels2 = 'xyz' "

something like
```
select A.id, A.field2,A.field3
from 	A inner join A_B on A.id = A_B.a_id 
			inner join B on A_B.b_id = B.id

where B.fiels2 = 'xyz' 
;
```


It would be harder if there wasn't a row (5,3) in table A_B, then you would exclude id 5 from table A because there's no corresponding key in A_B and thus no record that can have  B.fiels2 = 'xyz' 


You should probably get a beginners tuorial on SQL if tou want to write programs with a database backend :)

---

