---
title: "Vim in PyGtk"
date: 2011-05-16
forum: Programming Talk
---

### Post by ASK87 on 2011-05-16
Hi All,

I am trying to embed vim in pygtk. I have 2 problems. 

1. The rendering is not proper in vim. I don't know if its a problem is with vim configurations.

2. I am not able pass multiple arguments to vte in pygtk.
```

import vte
v= vte.Terminal()
v.fork_command("vim --servername PYGTK")

```
This makes the program hang and there is not output.

Appreciate the help.
Thanks

---

### Post by howefield on 2011-05-16
Thread moved to "*Programming Talk*"

Not a tutorial, think you'll get best help here.

---

