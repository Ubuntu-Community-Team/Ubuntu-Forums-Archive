---
title: "Python help (newbie)"
date: 2010-10-28
forum: Programming Talk
---

### Post by olddai on 2010-10-28
Have wrote out the following:

#!/usr/bin/env python
Months = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec']
DaysInMonth = [31,28,31,30,31,30,31,31,30,31,30,31]
for cntr in range(0,12):
    print '%s has %d days.'
(Months[cntr],DaysInMonth[cntr])

Saved it as days_months.py

But when called i just get the following:

gugan@computer:~$ ~/python_examples/days_months.py
%s has %d days.
%s has %d days.
%s has %d days.
%s has %d days.
%s has %d days.
%s has %d days.
%s has %d days.
%s has %d days.
%s has %d days.
%s has %d days.
%s has %d days.
%s has %d days.
gugan@computer:~$

Could someone tell this old newbie what i am doing wrong please.

---

### Post by olddai on 2010-10-28
I can't get the months nor the number of days to appear?

---

### Post by TiBaal89 on 2010-10-28
You just forgot a percent sign...  try:

```
print '%s has %d days.' % (Months[cntr],DaysInMonth[cntr])
```

Also, a general tip for posting code on a forum - use the 'code' tags.  It will preserve your indentation and whatnot (especially important for python code).

---

### Post by olddai on 2010-10-28
That was spot on and thanks TiBaal89. And i won't forget to use the 'code' tags in future either :P

---

