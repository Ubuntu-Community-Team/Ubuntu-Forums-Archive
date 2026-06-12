---
title: "Pretty Date in Python"
date: 2009-01-19
forum: Programming Talk
---

### Post by Achetar on 2009-01-19
I need a different dates based on what time it is now. So if it today I need, say, 1:28PM. But if that item is from yesterday (or the day before, etc) I need like January 19th, 2009. How can I do this in Python?

---

### Post by cudjoe on 2009-01-20
Just test the age of your item :

```

import datetime

def age(timestamp):
    today = datetime.datetime.today()
    return today - timestamp

def printdate(timestamp):
    age = age(timestamp)
    format = "%H:%M"
    if age.days > 1:
        format = "%d %m %y"
    print timestamp.strftime(format)

```

---

### Post by Achetar on 2009-01-22
I figured it out and it's basically what you said cudjoe. Thanks anyway though.

---

