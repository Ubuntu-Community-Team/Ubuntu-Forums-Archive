---
title: "[Python] Seconds past midnight"
date: 2011-05-23
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-23
In an old language which I programmed in before Python I was able to calculate seconds past midnight by using: time(seconds) Is there a feature in Python for this?

---

### Post by simeon87 on 2011-05-23
Have a look at the [datetime]("http://docs.python.org/library/datetime.html") module.

```
import datetime
a = datetime.datetime(2011,5,23)
b = a + datetime.timedelta(seconds=10)
```

---

### Post by LeDroid on 2012-06-01
a = datetime.datetime(2011,5,23,15,30,45)
# print seconds past midnight
print (a - datetime.datetime.min).seconds

# Should display 55845

---

