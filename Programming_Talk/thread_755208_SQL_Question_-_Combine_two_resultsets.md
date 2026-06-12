---
title: "SQL Question - Combine two resultsets"
date: 2008-04-14
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-04-14
I have one query which looks like this:

select result1, param1, param2
from sometable

select result2, param1, param2
from sometable

From this, I want to get this:

select (result2 - result1), param1, param2
from sometable

result2 and result1 will be real numbers so subtraction should work.  If not, could I get

select result2, result1, param1, param2 
from sometable

---

### Post by pmasiar on 2008-04-14
You need to JOIN tables, right? What are keys?

---

