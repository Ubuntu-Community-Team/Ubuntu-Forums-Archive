---
title: "Python - How to close browser windows opened by webbrowser.open()"
date: 2013-03-31
forum: Programming Talk
---

### Post by arcsin on 2013-03-31
I'm trying to open a webpage from a python script then close it after a set amount of time (or when the user presses a key).

However I'm not sure what would be the best way to close the browser window that webrowser.open() creates?

---

### Post by wojox on 2013-03-31
You could add ```
webrowser.close()
``` to the end of your func.

When you close the script the object should be destroyed automatically.

---

### Post by arcsin on 2013-03-31
> **wojox said:**
> You could add ```
webrowser.close()
``` to the end of your func.

When you close the script the object should be destroyed automatically.

Ok I tried this but it doesn't seem to work.

```
import webbrowser

webbrowser.open("http://www.google.co.uk")
webbrowser.close()


```

It comes up like this when I run it from terminal:

```

user@pc:~/Programming$ python test.py
Traceback (most recent call last):
  File "test.py", line 4, in <module>
    webbrowser.close()
AttributeError: 'module' object has no attribute 'close'
user@pc:~/Programming$ QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.


```

I also had to press the return key before it would finish executing the program.

---

