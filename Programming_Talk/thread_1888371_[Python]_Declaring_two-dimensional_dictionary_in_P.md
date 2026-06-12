---
title: "[Python] Declaring two-dimensional dictionary in Python"
date: 2011-11-29
forum: Programming Talk
---

### Post by kramer65 on 2011-11-29
Hello,

I am able to create a two dimensional dictonary by simply giving all its contents:
```
price_dict = {'1997-05-28': {'09:02:00': 74.54, '09:01:00': 77.22},
'1997-05-29': {'09:02:00': 76.98, '09:01:00': 77.34, '09:03:00':79.23},
'1997-05-30': {'09:03:00': 80.12, '09:01:00': 78.27, '09:02:00': 79.94}}

```
The thing is that I now want to declare an empty two-dimensional dictonary and then fill it using an iteration (from a Postgres-DB).

But when I try to do this:
```
price_dict = {}
price_dict['1997-02-03']['09:07:00'] = 5
```
I get an error saying: *KeyError: '1997-02-03'*

How would I be able to declare an empty two dimensional dictionary and then add values to it?

---

### Post by San_SS! on 2011-11-29
You can do something like this:

```


d = {}

for (first, second, value) in ...:
    d[first] = d.get(first, {})
    d[first][second] = value


```

You initialize the the dictionary under the first index in case it doesn't exist, and then you insert the element inside that dictionary.

---

### Post by kramer65 on 2011-11-29
The thing is that I take stuff from a DB and iterate over it. This is why I tried it like this:

```

open_dict = {}
sql = "SELECT datum, tijd, open FROM table;"
cur.execute(sql)
rows = cur.fetchall()
for row in rows:
    datum = row['datum'].strftime('%Y-%m-%d')
    tijd = row['tijd'].strftime('%H:%M:%S')
    open_dict[datum][tijd] = row['open']

```

So I can't really go over the records day by day and record all times per day. I get them record by record.

Any ideas to solve this?

---

### Post by San_SS! on 2011-11-29
Yes you can. Change:

```

open_dict[datum][tijd] = row['open']

```

for:

```

open_dict[datum] = open_dict.get(datum, {})
open_dict[datum][tijd] = row['open']

```

In that way, if you don't have a dictionary at datum position in open_dict it will be created empty then you insert in that dictionary at position tijd the value of row['open'], do you get it?. The whole problem is that you need to initialize the value of  open_dict[datum] to an empty dict in case it doesn't exist.

---

### Post by kramer65 on 2011-11-29
That is a great solution!

Thank you so much!

---

### Post by The Cog on 2011-11-30
> open_dict[datum] = open_dict.get(datum, {})
Does this create and immediately delete an unused dict every time open_dict already contains the datum key?

---

### Post by San_SS! on 2011-11-30
Yes, Python evaluates first the parameters so a new dict is created.

You made me think if performance could be improved and I have tried this 2 codes:

Code 1:
```

d = {0: 1}

for i in xrange(10 ** 7):
    d[0] = d.get(0, {})

```

vs.

Code 2:
```

d = {0: 1}
for i in range(10 ** 7):
    d[0] = d[0] if 0 in d else {}

```

And I've obtained the following results:

Code 1:
```

real	0m3.054s
user	0m3.040s
sys	0m0.010s

```

Code 2:
```

real	0m2.872s
user	0m2.760s
sys	0m0.110s

```

There is some improvement but not SO important. Anyways the new line is more expressive than the old, i would use it.

---

