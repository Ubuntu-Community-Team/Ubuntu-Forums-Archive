---
title: "SQL select top results"
date: 2009-06-17
forum: Programming Talk
---

### Post by wertyuiop408 on 2009-06-17
In a table of mine i have a list of numbers (random) and want to order them descending and select the top results to meet a number defined in a php variable.


example.
ID | numbers
-------------
1 | 12
2 | 52
3 | 78
4 | 2
5 | 9

and the number defined by the php variable is 90. The query would select UD 3 and ID 2 as they are the largest numbers.


Sorry if im not very clear, and thanks in advance

---

### Post by Tibuda on 2009-06-17
```
**select** *
**from** tablename
**order by** numbers **desc**
**limit** 2
```

I just don't understand what you want with "meet a number defined in a php variable".

---

### Post by Mirge on 2009-06-17
> **wertyuiop408 said:**
> In a table of mine i have a list of numbers (random) and want to order them descending and select the top results to meet a number defined in a php variable.


example.
ID | numbers
-------------
1 | 12
2 | 52
3 | 78
4 | 2
5 | 9

and the number defined by the php variable is 90. The query would select UD 3 and ID 2 as they are the largest numbers.


Sorry if im not very clear, and thanks in advance

Not real sure what you mean by the php variable either, but if you mean highest numbers that have a maximum value of lets say $max_value (PHP variable), then you'd do:

```

SELECT * FROM table_name WHERE numbers <= $max_value ORDER BY numbers DESC LIMIT 2

```

---

