---
title: "Python list problem"
date: 2012-07-22
forum: Programming Talk
---

### Post by Old-un on 2012-07-22
Have been following a tutorial from the Full Circle magazine concerning lists, but for some reason i can't understand it just won't work . The code is:

```

#! /usr/bin/python
Months = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec']
DaysInMonth = [31,28,31,30,31,30,31,31,30,31,30,31]
for cntr in range (0,12) :
    print '%s has %d days.' 
(Months[cntr], DaysInMonth[cntr])

```and the outout is:

old-un@ubuntu-linux-uk:~$ python ~/python_examples/calender.py
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
old-un@ubuntu-linux-uk:~$

Would someone take pity on this old-un and explain where i have gone wrong please.

---

### Post by MadCow108 on 2012-07-22
you probably want this:
```
print '%s has %d days.' % (Months[cntr], DaysInMonth[cntr])
```

% is a (kind of deprecated) string formatting operator similar to C's printf.

it teills it to insert the first argument Months[cntr] as a string in %s and the second as an integer into %d
see
[http://docs.python.org/library/stdtypes.html#string-formatting-operations](http://docs.python.org/library/stdtypes.html#string-formatting-operations)

a nicer way to do the loop would be using the zip function to directly iterate over both lists
```
for month, ndays in zip(Months, DayInMonth):
  print '%s has %d days' % (month, ndays)
```

---

### Post by Old-un on 2012-07-22
That was spot on MadCow108. Big thanks for the help!

---

### Post by trent.josephsen on 2012-07-22
MadCow mentioned that the % operator is "kind of deprecated" in this use -- the new way to do this is with the .format method.

```
print '{} has {} days'.format(month, ndays)
print '{0} has {1} days'.format(month, ndays) # positional indexing
```

You'll notice this method doesn't require different type specifiers for strings and integers, which generally makes a bit more sense for a strongly typed language like Python (the % format specifiers descend from C's printf).

---

