---
title: "Quick Python List-Dictionary conversion help"
date: 2008-03-03
forum: Programming Talk
---

### Post by ablegreen on 2008-03-03
Hi,
Suppose I have this list that contains tuples, and each tuple contains dictionaries:

> [('2008-01-27', {'in_month': False, 'day': 27, 'events': False}), ('2008-01-22', {'in_month': False, 'day': 22, 'events': False})]

How do I convert the dictionaries into tuples so that the list is like this:

> [('2008-01-27', (('in_month', False), ('day', 27), ('events', False))), ('2008-01-22', (('in_month', False), ('day', 22), ('events', False)))]

Thanks.

---

### Post by Wybiral on 2008-03-03
```

lst = [
    ('2008-01-27', {'in_month': False, 'day': 27, 'events': False}),
    ('2008-01-22', {'in_month': False, 'day': 22, 'events': False})
]

print [(a, tuple(b.items())) for a, b in lst]

```

---

### Post by ablegreen on 2008-03-03
Ok thanks I will try that out

---

