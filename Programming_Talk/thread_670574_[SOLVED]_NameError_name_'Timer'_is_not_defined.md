---
title: "[SOLVED] NameError: name 'Timer' is not defined"
date: 2008-01-17
forum: Programming Talk
---

### Post by mevets on 2008-01-17
I cannot seem to use Timers. I have been able to get them to work inside the shell, but not when I make a new .py file and make the timer inside a class. I suppose my problem is that when I go to make a Timer inside another class i made that isnt allowed.

It always tells me Timer is not defined when I run this:
```

import time
import threading

class MyClass:
    t=Timer(10,whatever)
    
    def whatever(self):
        print  "you got here!"
        return


```

---

### Post by Wybiral on 2008-01-17
"Timer" belongs in the "threading" namespace. Use: "threading.Timer()" instead of "Timer()"

EDIT:

Also, you need to start the thread too using "t.start()" after it's initialized.

---

### Post by mevets on 2008-01-17
Ah Thank you.

---

