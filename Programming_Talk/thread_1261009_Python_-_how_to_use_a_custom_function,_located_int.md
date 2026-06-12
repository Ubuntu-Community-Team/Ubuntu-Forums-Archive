---
title: "Python - how to use a custom function, located into another Python file ?"
date: 2009-09-08
forum: Programming Talk
---

### Post by credobyte on 2009-09-08
Ok, so - is it even possible to achieve this ? If so, what exactly I need to do to make it work ?
[B]
core.py[/B]
```
def say(str):
    print str
```

**main.py**
```
say("It works!")
```

---

### Post by Tony Flury on 2009-09-08
yes - so long as core.py is in your PYTHON_PATH (your current directory should be sufficient) then 

```

import core

say("It works!")

```

will work.

---

### Post by Bachstelze on 2009-09-08
Or even better, in order not to pollute your namespace:

```
from core import say

core.say("It works!")
```

---

### Post by DaithiF on 2009-09-08
either:
```
import core
core.say("hello")
```

or

```
from core import say
say("hello")

```

---

### Post by credobyte on 2009-09-08
Thank you, however, something doesn't work right .. 
Once I execute my main.py, all I get is a core.pyc ( new file ) and an error, stating that [COLOR=RoyalBlue]core is not defined[/COLOR].

Ehh ? :-k

**UPDATE ::** DaithiF, #1 example works like a charm .. others don't. Thank you :)

---

### Post by Bachstelze on 2009-09-08
> **Tony Flury said:**
> yes - so long as core.py is in your PYTHON_PATH (your current directory should be sufficient) then 

```

import core

say("It works!")

```

will work.

No, it will not. ;)

```
import core

core.say("It works!")
```

will.

*Never mind my first message, my brain is tired from the 4 hours of math this morning.*

---

### Post by DaithiF on 2009-09-08
> **credobyte said:**
> Thank you, however, something doesn't work right .. 
Once I execute my main.py, all I get is a core.pyc ( new file ) and an error, stating that [COLOR=RoyalBlue]core is not defined[/COLOR].

Ehh ? :-k

**UPDATE ::** DaithiF, #1 example works like a charm .. others don't. Thank you :)

my #2 example works too!  :)

the .pyc file is just a compiled version of the core.py module, which python creates as a convenience to allow it to import the module more efficiently next time.

---

### Post by credobyte on 2009-09-08
> **DaithiF said:**
> my #2 example works too!  :)

the .pyc file is just a compiled version of the core.py module, which python creates as a convenience to allow it to import the module more efficiently next time.

Ok, I see. Thanks for an explanation ( .pyc ) :)

---

