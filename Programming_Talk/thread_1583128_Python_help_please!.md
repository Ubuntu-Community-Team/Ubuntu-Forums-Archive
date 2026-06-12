---
title: "Python help please!"
date: 2010-09-27
forum: Programming Talk
---

### Post by olddai on 2010-09-27
Have only just started to learn Python and can't get this program to execute. Hope someone will take pity on me and be able to help. 

#!/usr/bin/env python

Months =
['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec']
DaysInMonth =
[31,28,31,30,31,30,31,31,30,31,30,31]
for cntr in range(0,12):
    print '%s has %d' % 
(Months[cntr],DaysInMonth[cntr])

Can't see where i'm going wrong. Thanks

---

### Post by schauerlich on 2010-09-27
Unlike most other languages, whitespace is important in python. That means you can't put random newlines and not indent and have it work correctly. This works for me. All I did was rearrange what was already there:

```
Months = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec']
DaysInMonth = [31,28,31,30,31,30,31,31,30,31,30,31]
for cntr in range(0,12):
	print '%s has %d' %  (Months[cntr],DaysInMonth[cntr])

```

---

### Post by olddai on 2010-09-27
That was spot on and something that i will remember from now on! Very big thanks schauerlich.

---

### Post by schauerlich on 2010-09-27
Also, for something like this, you might want to look into [dictionaries](http://docs.python.org/library/stdtypes.html#mapping-types-dict).

```
daysByMonth = {
    'Jan' : 31,
    'Feb' : 28,
    # ...
    'Dec' : 31,
}
```

---

### Post by juancarlospaco on 2010-09-27
I think if you use

Thing =

allways get an error, you need to make it equal to something.

---

### Post by OgreProgrammer on 2010-09-28
and start using print in the future python 3 format. 

print('this is the way of the future')
print('olddai is the %d best programmer in the world') % (number)

print 'this is the way of the past'

it will make the transition easier for you when it comes.

---

