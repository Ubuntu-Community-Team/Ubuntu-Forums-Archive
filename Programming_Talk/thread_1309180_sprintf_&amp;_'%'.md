---
title: "sprintf &amp; '%'"
date: 2009-11-01
forum: Programming Talk
---

### Post by matmatmat on 2009-11-01
How do i represent the '%' character? I need to create a SQL query:
```

SELECT * FROM people where name LIKE '%xxx%'

```
The 'xxx' bit will be formatted ('%s'), how would I do this?

---

### Post by albandy on 2009-11-01
\%

---

### Post by miklcct on 2009-11-01
> **albandy said:**
> \%

You are wrong. It should be "%%"

---

### Post by albandy on 2009-11-01
> **miklcct said:**
> You are wrong. It should be "%%"

[http://dev.mysql.com/doc/refman/5.0/en/string-syntax.html](http://dev.mysql.com/doc/refman/5.0/en/string-syntax.html)

---

### Post by slakkie on 2009-11-01
> **albandy said:**
> [http://dev.mysql.com/doc/refman/5.0/en/string-syntax.html](http://dev.mysql.com/doc/refman/5.0/en/string-syntax.html)

Still wrong. \% is to represent the % as a literal character in MySQL. '\%%' whould match on anything starting with %

With printf, to get the % character, you should use %%.

So making \% is mysql with printf would be:

printf "\%%"

---

### Post by albandy on 2009-11-01
> **slakkie said:**
> Still wrong. \% is to represent the % as a literal character in MySQL. '\%%' whould match on anything starting with %

With printf, to get the % character, you should use %%.

So making \% is mysql with printf would be:

printf "\%%"

He's asking how to represent the % character. So I answered it, I'm not writing the query.

For example if he/she has entries in a table field like "Our percentages are 20% of some thing" the query should be
select * from table where field like '%20\%%';

Edit:
sorry I didn't realize that he was asking how to write it throught sprintf, I thought he was asking how to introduce the % character in a mysql query, of course, if he want to use the % character in the query he should scape char for sprintf and the scape char for mysql query, for example:

select * from table where fielad like '\%20\\%\%'

---

### Post by slakkie on 2009-11-01
it should be (in bash):

```

$ printf "select * from table where field = '%%%s%%'" value
select * from table where field = '%value%'
```

---

### Post by albandy on 2009-11-01
> **slakkie said:**
> it should be (in bash):

```

$ printf "select * from table where field = '%%%s%%'" value
select * from table where field = '%value%'
```


VAR=HELLO
printf "select * from table where field ='\045$VAR\045'"
result:
select * from table where field ='%HELLO%'

---

