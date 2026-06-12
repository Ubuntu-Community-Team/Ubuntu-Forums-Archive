---
title: "Python 2.6.6 Help!!! QuickScope Script!"
date: 2011-03-14
forum: Programming Talk
---

### Post by GosthShadow on 2011-03-14
I would like to make an Quick Scope script for MW2 this is where i stop
```
import SendKeys
import time

while True:
    raw_input('QS')
    SendKeys.SendKeys("""
        {RWIN}
        {PAUSE .75}
        {LWIN}
        {PAUSE .25}
        {RWIN}

    """)
    

```

I would like to be able to run this script in background, and raw_input() would be triggered by right mouseclick.
I'm on windows xp...

---

### Post by GosthShadow on 2011-03-15
*bump*

---

