---
title: "SQL wildcard query question"
date: 2009-10-02
forum: Programming Talk
---

### Post by tc101 on 2009-10-02
I can query 

Select * from tablename where fieldname in ('mike','bill','joe')

Is there something similar for wildcards?  What is the shortest way to
say

Select * from tablename 
where fieldname like '%mike%'  
or  fieldname like '%bill%'  
or  fieldname like '%joe%'

---

### Post by unutbu on 2009-10-02
```
select * from tablename where fieldname regexp 'mike|bill|joe';
```

---

### Post by Tony Flury on 2009-10-03
it depends on your dialect of SQL.

To the best of my knowledge for instance ORACLE SQL, MS Access SQL and many other Dialects (and indeed ANSI SQL) does not have the regexp comparator.

In Oracle you will need to do what you orginally suggested
```

Select * from tablename
where fieldname like '%mike%'
or fieldname like '%bill%'
or fieldname like '%joe%' 

```

Disclaimer : it has been a while since i did any Oracle SQL development so they might have extended the syntax.

---

### Post by tc101 on 2009-10-03
It doesn't work in SQL Server, which is what I am using.  I should have said that in the original post.

---

