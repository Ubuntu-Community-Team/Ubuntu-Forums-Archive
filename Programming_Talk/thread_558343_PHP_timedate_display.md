---
title: "PHP time/date display"
date: 2007-09-23
forum: Programming Talk
---

### Post by woodsonoversoul on 2007-09-23
use the code:
```
date("m/d/y g:i a", $row[5])
```

To display the datetime stored in row[5] which is :2007-09-23 20:13:09

The output is : 12/31/69 6:33 pm

Why?

---

### Post by DoktorSeven on 2007-09-23
The second value has to be a timestamp.  To convert strings to timestamps, use **strtotime**.

---

### Post by Takuhari on 2007-10-16
i really need to know the answer to thiz problem also>_<:lolflag:

---

### Post by Takuhari on 2007-10-16
> **DoktorSeven said:**
> The second value has to be a timestamp.  To convert strings to timestamps, use **strtotime**.

I have no klue what this means...>_< can you explain it?..
btw im a noob^^*:confused:

---

### Post by slavik on 2007-10-16
strtotime is a php function, go to php.net and look it up

---

