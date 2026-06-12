---
title: "datetime.timedelta"
date: 2010-06-05
forum: Programming Talk
---

### Post by xaegis on 2010-06-05
I was reading about this (timedelta) class in the Python API and I cant really understand it enough to make use of it. What is this class for?

---

### Post by wmcbrine on 2010-06-05
Basically, you give it an interval of time, and it gives you back something that you can add to a datetime object, yielding a new datetime object.

---

### Post by soltanis on 2010-06-05
It's for representing differences in time through a standardized interface (though if you asked me, using an integer or double would've been smarter). So if you subtract two times, you get a timedelta. And you can compare two timedeltas to see which is greater, or if they are equal.

---

### Post by xaegis on 2010-06-05
Ok, thanks guys!

---

