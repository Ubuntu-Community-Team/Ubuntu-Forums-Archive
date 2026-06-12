---
title: "Get difference between timezone and GMT from textstring with Python"
date: 2009-07-15
forum: Programming Talk
---

### Post by Krijk on 2009-07-15
I've got the following string "**Tue, 07 Jul 2009 10:54:58 EDT**" and want to get the difference with GMT (which is 4 hours)

I can convert it with time.strptime and time.strftime (%z is Timezone)to a time-tuple **(2009, 7, 7, 14, 54, 58, 1, 188, 0)** but it is in GMT. 

How can I get the difference with GMT? (preferably with a standard module)

---

