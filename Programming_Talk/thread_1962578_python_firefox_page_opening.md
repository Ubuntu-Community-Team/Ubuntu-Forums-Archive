---
title: "python firefox page opening"
date: 2012-04-21
forum: Programming Talk
---

### Post by AnojiRox on 2012-04-21
hi,
I have just made a daemon in python that knows what keys have been pressed. if you press "brz" then it opens firefox using
```
os.system("firefox")
```
only problem is, I want it to change the web page every ten seconds. for example, when you first open it, it opens ubuntuforums.com, then after ten seconds the page changes to google.com, say. ten seconds after that, it changes back. anyone know how to do this?

---

### Post by digrejzo on 2012-04-21
Not sure if this will help, but maybe you can find it useful:

```

import time

time.sleep(10) #sleep for 10 seconds
#execute something else after 10 seconds

```

Again, you're maybe looking for something different.

---

### Post by LemursDontExist on 2012-04-25
Look into [Selenium]("http://code.google.com/p/selenium/").  I think it provides the sort of browser automation you're looking for.

Alternatively, Chromium has automation more or less built in, complete with a [Python interface]("http://www.chromium.org/developers/testing/pyauto").

---

