---
title: "Reverting date from Time.to_s (RUBY)"
date: 2010-03-22
forum: Programming Talk
---

### Post by utsavgupta on 2010-03-22
I receive the dates from Twitter in the following format "Mon Mar 22 04:42:17 +0000 2010"

Now how can I create a time object from this string... ie Obj.year=2010, Obj.month=3... etc etc


Regards

Utsav Gupta

---

### Post by stylishpants on 2010-03-22
```
require 'time'

t = Time.parse("Mon Mar 22 04:42:17 +0000 2010")
puts t.year
puts t.month

```

---

