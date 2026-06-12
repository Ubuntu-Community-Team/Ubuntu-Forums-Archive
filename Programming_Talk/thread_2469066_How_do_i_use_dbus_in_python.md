---
title: "How do i use dbus in python?"
date: 2021-11-18
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2021-11-18
i have read the start of the tutorial a dozen times and all i understand is the 1st couple lines of code

[https://i.imgur.com/ZhgSYLg.png](https://i.imgur.com/ZhgSYLg.png)

My code is in the top left, the command to do what i want is on the top right

This should be simple to do but i can't fire out what i am doing and have a headache from banging my head at this point and feel like say screw the library and using a shell command from python

---

### Post by pqwoerituytrueiwoq on 2021-11-23
The reason i was not able to figure it out was the property name in the widget is pass and using that word properly as you would any other word  will cause a Syntax error
This causes a syntax error cause of the word 'pass' even though the usage is correct for the given task, if i did not need to use that word i would not have had a issue, modifying the code of the dbus service i am connection to to not use the word pass fixes it
```

from dbus import SessionBus
from sys import argv
if len(sys.argv) == 1:
    print("no input given")
    quit()
bar=SessionBus().get_object("org.kde.plasma.doityourselfbar","/id_"+sys.argv[1])
bar.pass('Output_string')
----------
from pydbus import SessionBus
from sys import argv
if len(sys.argv) == 1:
    print("no input given")
    quit()
bar=SessionBus().get("org.kde.plasma.doityourselfbar","/id_"+sys.argv[1])
bar.pass('Output_string')

```

---

