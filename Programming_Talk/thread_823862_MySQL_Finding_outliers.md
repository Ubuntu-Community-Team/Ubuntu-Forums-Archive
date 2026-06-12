---
title: "MySQL: Finding outliers"
date: 2008-06-09
forum: Programming Talk
---

### Post by altonbr on 2008-06-09
If I have two tables like so:
--------------------
|     Students     |
| id | name | s_id |
-------------------
|  1 | Joe  | 2   |
|  2 | Joel | 1   | 
|  3 | Bret | 1   | 

where s_id = schools.id

-------------------
|    Schools      |
| id |    name    |
-------------------
|  1 | PCVS       |
|  2 | LDSA       |
|  3 | RSDS       |
|  4 | ODSA       |

How do I only return an id of 3 and 4, meaning they don't have any matching students?

LEFT JOIN returns 1,2 while RIGHT JOIN returns 1,2,3,4.

```
SELECT `schools`.`id`
FROM `students`
LEFT JOIN `schools` # or RIGHT JOIN
ON `students`.`s_id` = `schools`.`id`

```

---

### Post by aks44 on 2008-06-09
Tip: WHERE ... NOT IN ...

Homework?

---

### Post by LoneWolfJack on 2008-06-09
```
SELECT schools.id FROM schools WHERE 
(SELECT COUNT(*) FROM students WHERE students.s_id=schools.id)=0
```

at least give me a thanky for doing your homework ;-)

---

### Post by forger on 2008-06-09
here are some more examples with IN():
[http://dev.mysql.com/doc/refman/5.0/en/comparison-operators.html#function_in](http://dev.mysql.com/doc/refman/5.0/en/comparison-operators.html#function_in)

---

### Post by altonbr on 2008-06-09
No, its actually a pretty big database I'm working on, I'm just not a database programmer :S.

I modified the table names and simplified it for my example. I work at a school-board part time, so that's why I chose students and schools :P

Thanks for the tips everyone :)

---

### Post by altonbr on 2008-06-09
I tried this:
```
SELECT `schools`.`id` FROM `schools`, `students` NOT IN (`students`.`s_id`)
```

However, it looks like you have to statically set all of the `students`.`s_id`s, which obviously would not work as this is a very large DB.

```
SELECT `schools`.`id` FROM `schools`, `students` NOT IN ('1','2')
```

---

### Post by altonbr on 2008-06-09
Oh wait, it appears LoneWolfJack DID do my 'homework' :P. Thank you everyone :)

Now that only thing that confuses me is that it is using COUNT(), how many times does it return zero and and yet get the matching `schools`.`id`?

---

### Post by LoneWolfJack on 2008-06-09
mysql first gets the count of students per school through the subquery, then it will select all schools that have 0 students.

you could also do this if you like it better
> 
SELECT schools.id FROM schools WHERE schools.id 
IN(SELECT s_id FROM students GROUP BY s_id)


if you really have many datasets (like at least several 100k) you could play around with both variants and see which yields the better performance. setting your indexes right plays a key (no pun intended) role here.

if you are a performance junkie (like me), you will also try running query and subquery seperatedly.

---

