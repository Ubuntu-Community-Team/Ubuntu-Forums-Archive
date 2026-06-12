---
title: "[SOLVED] python open file with fauvorite application"
date: 2008-12-16
forum: Programming Talk
---

### Post by giuspen on 2008-12-16
I found some time ago, reading the python reference, that there is a module to open a file with the fauvorite application (same as double-clicking through the file manager), now that I need to use it I can't find anymore :(
Does anybody can help me?

---

### Post by cszikszoy on 2008-12-16
What you want is xdg-open.  xdg-open opens files or links in the default application.  Try it on text files, http links, music files etc etc.

Try this in python:
```

import os
cmd = 'xdg-open http://www.google.com'
os.system(cmd)

```

---

### Post by giuspen on 2008-12-17
Finally I found out that there is a function to start a file in the module "os" of python, it's "startfile":
[PHP]import os
os.startfile(path)[/PHP]
but this seems to exist only for windows, so it's absolutely unuseful for me. 
The solution of cszikszoy (launch through the shell) seems the only way.

---

