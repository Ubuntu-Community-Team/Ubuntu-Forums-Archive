---
title: "Python: import fails outside module, while working inside"
date: 2009-01-20
forum: Programming Talk
---

### Post by cudjoe on 2009-01-20
This problem is puzzling me. It is not easy to describe, thus hard to search on the web.

I have a schedule package.
It contains a third-party library called **calendar**.

**schedule/calendar/__init__.py** (empty)
**schedule/calendar/format.py** :
```

class Format:
	"""
	"""
```

**schedule/calendar/cal.py** :
```
from calendar.format import Format
f = Format()

```


If I use this calendar within the schedule package, it works:

**schedule/__init__.py** (empty)
**schedule/event.py** :
```
import calendar.cal

class Event:
	"""
	"""
```

**schedule/working.py** :
```

from event import Event

ev = Event()
```


But from outside the schedule package, it does not work.

**notworking.py**
```
from schedule.event import Event

ev = Event()
```

```
Traceback (most recent call last):
  File "notworking.py", line 1, in <module>
    from schedule.event import Event
  File "./schedule/event.py", line 1, in <module>
    import calendar.cal
  File "./schedule/calendar/cal.py", line 1, in <module>
    from calendar.format import Format
ImportError: No module named format
```

In theory, I should not have to modify anything in the calendar module since it is a third party software.

Thank you for your help.

(I attached the hierarchy of files)

---

### Post by Paul Miller on 2009-01-20
Are these packages on your PATH or PYTHONPATH?  Try

**maybe_working.py**
[php]
import sys
sys.path.append ("/path/to/the/package")
del sys

from schedule.event import Event

ev = Event()
[/php]

---

### Post by cudjoe on 2009-01-20
Thanks for your help.

I have the same error adding it the path:

```
import sys, os
sys.path.append (os.path.join(os.getcwd(), "schedule/calendar") )
del sys

from schedule.event import Event

ev = Event()
```

Again, in theory, I guess I should not have to worry about every schedule sub-packages...

---

### Post by unutbu on 2009-01-20
If you run 
[PHP]#!/usr/bin/env python
import calendar
print calendar
import calendar.format[/PHP]

from outside the schedule directory, you will see 

```
<module 'calendar' from '**/usr/lib/python2.5/calendar.pyc**'>
Traceback (most recent call last):
  File "/home/user/pybin/test.py", line 4, in <module>
    import calendar.format
ImportError: No module named format
```

Notice that the standard installation of python2.5 includes a module named calendar.

When you run working.py (from within the schedule directory), schedule is placed at the head of sys.path, so python finds your calendar module first (and then loads it).

When you run notworking.py (from outside the schedule directory), schedule is not at the head of sys.path, so python finds its own calendar module (/usr/lib/python2.5/calendar.pyc) first. 

This is why the script does not work from outside the schedule directory.

Renaming your calendar directory to something else should fix the problem.

---

### Post by cudjoe on 2009-01-21
I renamed the module. 
Strange.
It still works from inside package schedule
and still doesn't from outside.

Outside, I run:
```

>>> import schedule.calendrier
>>> print schedule.calendrier
<module 'schedule.calendrier' from 'schedule/calendrier/__init__.pyc'>
>>> import schedule.calendrier.format

```

But running **notworking.py** :
```

Traceback (most recent call last):
  File "notworking.py", line 1, in <module>
    from schedule.event import Event
  File "schedule/event.py", line 1, in <module>
    import calendrier.cal
  File "schedule/calendrier/cal.py", line 1, in <module>
    from calendrier.format import Format
ImportError: No module named calendrier.format

```

---

### Post by unutbu on 2009-01-21
You have at least 2 options:

[list]
[*]**Option 1**: In cal.py change```

from calendrier.format import Format
```
to```

from schedule.calendrier.format import Format
```
and in event.py change
```
import calendrier.cal
```
to```

import schedule.calendrier.cal
```
[*]**Option 2**: You could edit ~/.profile
If you have not defined a PYTHONPATH, then add this line:
```

export PYTHONPATH=/path/to/schedule
```
Change /path/to/schedule to the correct path.

if you have defined a PYTHONPATH, then add
```

PYTHONPATH=$PYTHONPATH:/path/to/schedule
export PYTHONPATH
```

If you make this change, then you can keep your import statements as they are, without adding 'schedule':
```

from calendrier.format import Format
```
Log out and log back in to make the new PYTHONPATH effective.
[/list]

If you use either of these options, it is possible to change calendrier back to calendar, but since this would mask your ability to reach the standard calendar module, I would suggest you keep the module names distinct.

---

### Post by cudjoe on 2009-01-21
Thank you very much unutbu !

It works, actually using this outside schedule:

```

import sys, os
sys.path.append (os.path.join(os.getcwd(), "schedule") )

from schedule.event import Event

ev = Event()
```


while it did not work adding "**schedule/calendar**" as I tried previously.


I hope those posts can help more developers. Even though it is not easy to tag / reference...

---

