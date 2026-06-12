---
title: "python time with milliseconds"
date: 2007-08-29
forum: Programming Talk
---

### Post by zero-9376 on 2007-08-29
Hi, im trying to create a string which i will use to name files, im recording data and want to name the file based on the current time of day. the problem is that i need better than 1 second accuracy so this is what i have done...comments/suggestions please

import time
time_now_sec = time.mktime(time.localtime())
time_now_mic = time.time()
time_str = time.asctime()
milli = time_now_mic - time_now_sec
print time_str,".",milli

please not that i started learning python yesturday

thanks

---

### Post by zero-9376 on 2007-08-29
if someone can tell me whether this is correct, or if there is a better way it would be greatly appreciated

---

### Post by pmasiar on 2007-08-29
google fond this: [http://mail.python.org/pipermail/python-list/2003-November/235548.html](http://mail.python.org/pipermail/python-list/2003-November/235548.html)

---

### Post by dwblas on 2007-08-29
Python's datetime is good to milli-seconds on Windohs and micro-seconds on Linux.  [http://effbot.org/librarybook/datetime.htm](http://effbot.org/librarybook/datetime.htm)
import time
import datetime
start_time = datetime.datetime.now()
time.sleep( 2 )
print "difference =", datetime.datetime.now() - start_time

---

