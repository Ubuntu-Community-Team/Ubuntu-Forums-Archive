---
title: "Python timedelta"
date: 2007-12-09
forum: Programming Talk
---

### Post by mevets on 2007-12-09
I am using a timedelta to figure out how many seconds there are left until my alarm has to go off. I can use .days and .weeks fine,but i guess there is not .hours and .seconds. How could I get the equivelant of .hours and seconds?
```

        fullNow = datetime.datetime.now()
        now = datetime.datetime(fullNow.year, fullNow.month, fullNow.day, fullNow.hour, fullNow.minute)
        diff = alarm - now
        secs = (diff.days*86400) + (diff.hours*3600) + (diff.minutes*60)  + diff.seconds

```

---

### Post by Martin Witte on 2007-12-09
```
import datetime

now = datetime.datetime.now()
alarm = datetime.datetime(2007, 12, 9, 17, 0, 0, 0)
diff = alarm - now
print diff.seconds

```
see [http://docs.python.org/lib/datetime-timedelta.html](http://docs.python.org/lib/datetime-timedelta.html)

---

