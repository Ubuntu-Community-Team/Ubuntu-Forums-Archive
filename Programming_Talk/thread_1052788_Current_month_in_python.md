---
title: "Current month in python"
date: 2009-01-28
forum: Programming Talk
---

### Post by talsemgeest on 2009-01-28
Hi, I'm just doing a bit of playing around in python, and I have just about finished it. The only problem is, even with all my googling around, I can't find a way to get the number of the current month into my program. It would be best if I could assign the number of the month (i.e. 1 for january, 6 for June etc...) to a variable, like "month" for example.

---

### Post by ibutho on 2009-01-28
I am not really a python expert, but I think you could use a list for something like this. You could then use indexing when trying to access each element in the list e.g. for January, it would be something like months[0] and December months[11].

---

### Post by myrtle1908 on 2009-01-28
I'm no Python expert either but this seems to work  ...

```
import datetime

month = datetime.datetime.now().strftime("%m")
print month
```

Note: datetime - a library module for Python 2.3

---

### Post by talsemgeest on 2009-01-28
> **myrtle1908 said:**
> I'm no Python expert either but this seems to work  ...

```
import datetime

month = datetime.datetime.now().strftime("%m")
print month
```

Note: datetime - a library module for Python 2.3
Awesome, this seems to work nicely. Thank you for your help ibutho and myrtle1908!

---

