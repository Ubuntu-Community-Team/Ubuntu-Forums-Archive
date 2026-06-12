---
title: "Need help with MySQL select"
date: 2010-08-03
forum: Programming Talk
---

### Post by AndyBoy_LV on 2010-08-03
Hi!

I have a database that contains names and surnames in it. I need to write a SELECT that would return me a count of surnames for each letter of the alphabet. In other words, i need to get something like that:

A | B | C | D | E |..
0 | 5 | 3 | 4 | 1 | ...

I can get results for each separate letter by executing ```
SELECT COUNT(SURNAME) as A FROM USERS WHERE SURNAME LIKE '%A'
```, but that would mean executing ~30 selects. Is there a way to combine all these selects at once?

---

### Post by Some Penguin on 2010-08-03
Something like

```

SELECT SUBSTR(surname, 1, 1) AS firstch, count(*)  FROM users GROUP BY firstch

```

should work.

---

### Post by AndyBoy_LV on 2010-08-03
> **Some Penguin said:**
> Something like

```

SELECT SUBSTR(surname, 1, 1) AS firstch, count(*)  FROM users GROUP BY firstch

```

should work.


Thank you very much, that did the job ;)

---

