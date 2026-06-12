---
title: "exception handling in python"
date: 2013-03-25
forum: Programming Talk
---

### Post by wingnut2626 on 2013-03-25
```
import time


from sys import exit


readable_data = []


data_for_computations = []


def GetCount():
    print "What is the current count?"
    count = raw_input(">")
    readable_data.append(time.ctime())
    readable_data.append(count)
    
    data_for_computations.append(time.time())
    data_for_computations.append(count)
    
    print readable_data
    print data_for_computations
    
while 1 == 1:
    GetCount()
    
    try:




        print "The number of seconds elapsed since the last count is ",  int(time.time()) - int(data_for_computations[-4])
    except IndexError:
        continue
    finally:
        pass

```

Why isnt the Index Error handled the first time the list is populated?  The program crashes.....

---

### Post by Tony Flury on 2013-03-25
How does it crash - what error message do you get ?

---

### Post by wingnut2626 on 2013-03-25
It raises the Index Error that the index is out of the list range....I know that it will be on program execution, because i have to get to a point where i have enough items in the list to compute line 27.........shouldnt the 'try/except' block handle that?

---

### Post by Tony Flury on 2013-03-25
How many times does your code prompt you for the data ?

---

### Post by wingnut2626 on 2013-03-25
Once.  I ended up removing the try block

I added:

if len(data_for_computations) >= 4

as a prelude to line 27 on....

---

### Post by wingnut2626 on 2013-03-25
where is the option to mark the thread as solved?

---

### Post by LuisGMarine on 2013-03-27
Should be an option on the top tool bar called "Thread Tools"

---

### Post by ofnuts on 2013-03-27
> **LuisGMarine said:**
> Should be an option on the top tool bar called "Thread Tools"
There is a problem whith this since they migrated to the new software. As a workaround you have to edit the title of the first post directly.

---

