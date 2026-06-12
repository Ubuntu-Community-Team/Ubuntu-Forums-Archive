---
title: "[python] how do i get the local time from my computer"
date: 2009-06-16
forum: Programming Talk
---

### Post by xZachtmx on 2009-06-16
ok i want to get the time in this type of format from my computer 

12:00

but i dont know how to do that in python...?

---

### Post by unutbu on 2009-06-16
[PHP]
#!/usr/bin/env python
import time
# Two-digit hour in 24-hour format
print(time.strftime('%H:%M'))

# Or you can use the datetime module
import datetime
print(datetime.datetime.now().strftime('%H:%M'))[/PHP]

See [http://au2.php.net/strftime](http://au2.php.net/strftime) for a synopsis of valid codes you can use with strftime.

---

### Post by xZachtmx on 2009-06-16
thanks.  Im making a little animated desktop  alarm clock widget so this is kinda important :p

---

