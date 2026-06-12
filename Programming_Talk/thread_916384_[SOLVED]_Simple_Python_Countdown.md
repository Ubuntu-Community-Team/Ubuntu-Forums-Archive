---
title: "[SOLVED] Simple Python Countdown"
date: 2008-09-10
forum: Programming Talk
---

### Post by easybake on 2008-09-10
I know very little about python language but I found this simple script to give a countdown only in number of days. But i was wondering if someone knows how I could get this do hours and minutes as well. Any help would be great.

Here is the script.```

#!/usr/bin/python
import datetime
diff = datetime.datetime(2008, 9, 25) - datetime.datetime.today()
print diff.days,
```

---

### Post by ghostdog74 on 2008-09-10
> **easybake said:**
> I know very little about python language but I found this simple script to give a countdown only in number of days. But i was wondering if someone knows how I could get this do hours and minutes as well. Any help would be great.

Here is the script.```

#!/usr/bin/python
import datetime
diff = datetime.datetime(2008, 9, 25) - datetime.datetime.today()
print diff.days,
```

since you don't know much about python, look up the docs for [datetime](http://docs.python.org/lib/datetime-datetime.html). you can add in hours,min and seconds to datetime object when you instantiate it.
```

diff = datetime.datetime(2008, 9, 25,11,23,55) - datetime.datetime.today()
help(diff)
print diff.seconds

```

---

### Post by easybake on 2008-09-10
> **ghostdog74 said:**
> since you don't know much about python, look up the docs for [datetime](http://docs.python.org/lib/datetime-datetime.html). you can add in hours,min and seconds to datetime object when you instantiate it.
```

diff = datetime.datetime(2008, 9, 25,11,23,55) - datetime.datetime.today()
help(diff)
print diff.seconds

```

Perfect exactly what I was looking for. I had no idea where to look. Thanks a lot.

---

### Post by easybake on 2008-09-11
Update: I ended up using this to give day, hour, and minute.
```
#!/usr/bin/python
import datetime
diff = datetime.datetime(2009, 2, 12) - datetime.datetime.today()
print diff.days,"d ", diff.seconds/60/60,"h ", diff.seconds/60 - (diff.seconds/60/60 * 60),"m "
```

---

