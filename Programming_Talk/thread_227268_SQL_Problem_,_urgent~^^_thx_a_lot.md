---
title: "SQL Problem , urgent~^^ thx a lot"
date: 2006-08-01
forum: Programming Talk
---

### Post by 008325 on 2006-08-01
i have two table 

Table 1
==========
P_No , P_Phone ( both are pk )


Table 2
=========
P_No , P_Name 

, now i want to write a sql to findout the P_No that exactly

match P_Phone ( one to many case ) ...?

E.g

Table 1
==========
1 , 123456
1 , 123457

Table 2
=========
1 , John 

how can i find out the number 1 that exactly match with 

name = join and phone = 123456 and phone = 123457 ???

thx a lot

---

### Post by 008325 on 2006-08-01
P.S , i am using mysql , there have't INTERSECT...

---

### Post by LordHunter317 on 2006-08-01
You can do something like this, if I understand you:```
SELECT DISTINCT p_no 
FROM table2 t2 INNER JOIN table1 t1 USING (p_No)
WHERE p_Name = 'John' AND (p_Phone = '123456' OR p_Phone = '123457')
```

---

### Post by 008325 on 2006-08-01
> **LordHunter317 said:**
> You can do something like this, if I understand you:```
SELECT DISTINCT p_no 
FROM table2 t2 INNER JOIN table1 t1 USING (p_No)
WHERE p_Name = 'John' AND (p_Phone = '123456' OR p_Phone = '123457')
```


sorry , but i still get the result including p_Phone = '123457' but not including p_Phone = '123456'

---

### Post by ifokkema on 2006-08-01
> **008325 said:**
> sorry , but i still get the result including p_Phone = '123457' but not including p_Phone = '123456'
You may need to clearify your question. The example above returns the P_No values that correspond to an entry with P_Name = "John" and P_Phone values both 123456 and 123457. That would be consistent with an INTERSECT of the two phone numbers. What is it that you want then?

---

### Post by 008325 on 2006-08-01
> **ifokkema said:**
> You may need to clearify your question. The example above returns the P_No values that correspond to an entry with P_Name = "John" and P_Phone values both 123456 and 123457. That would be consistent with an INTERSECT of the two phone numbers. What is it that you want then?

i am doing a searching function , i let the user searching by the phone , it can select one or more than one phone number , it also can inter the data ( ssuch as name , etc ) to reduce the range of the result ...

so... iwant to use the intersect such as 
select P_No from table2 where phone = "XXXX"
INTERSECT
select P_No from table2 where phone = "YYYY"
INTERSECT 
select P_No from table where Name = "ZZZZ"


however , MYSQL doesn;t have any intersect function ?!

---

### Post by indytim on 2006-08-01
Try something like this:

```

if(strlen($phone_in)>0)
{
$sq1="select Table2.P_Name from Table1, Table2 where Table1.P_Phone='$phone_in' 
and Table2.P_No=Table1.P_No";
}
elseif(strlen($name_in)>0)
{
$sq1="select Table1.P_Phone from Table1, Table2 where
Table2.P_Name='$name_in' and Table1.P_No=Table2.P_No";
}
if(strlen($sq1)>0)
{
$res=mysql_query($sq1);
blah-blah-blah
}

Hope this helps,

IndyTim

```

---

### Post by 008325 on 2006-08-02
push o.o

---

### Post by LordHunter317 on 2006-08-03
The query I posted above is functionally equivalent to the INTERSECT query you listed.

---

### Post by 008325 on 2006-08-03
> **LordHunter317 said:**
> The query I posted above is functionally equivalent to the INTERSECT query you listed.

sorry , it still can not get the exactly result 

just John = 123456 OR john = 234556

if someone want to search the exactly case ...it cannot

e.g search someone call JOHN , 

and the phone MUST = 123456 AND 23456

, if i am using your SQL , 

it get the JOHN = 123456 OR JOHN = 23456

but while using the intersect sql , it works

---

### Post by ifokkema on 2006-08-03
You're right... it doesn't work. I could swear my initial test showed it did. Anyway, here it is:
```
SELECT t2.P_No, t2.P_Name FROM table2 t2 LEFT JOIN table1 t1a USING (P_No) LEFT JOIN table1 t1b USING (P_No) WHERE t2.P_Name = 'John' AND t1a.P_Phone = '123456' AND t1b.P_Phone = '123457';
```

---

