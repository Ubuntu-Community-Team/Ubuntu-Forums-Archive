---
title: "[SOLVED] [bash]+[python]Sh error: end of file unexpected"
date: 2008-06-29
forum: Programming Talk
---

### Post by -grubby on 2008-06-29
OK, I'm making as simple Python run dialouge, and when running it the only clue that something went wrong is:

```

sh: Syntax error: end of file unexpected

```

The source of the app is:

[php]
import os

inputRun = os.popen("zenity --entry --text=Input\ a\ program\ to\ run --title=Run")
run = os.system(str(inputRun))
[/php]

---

### Post by dn_desaku on 2008-06-29
```
import os 

inputRun = os.popen("zenity --entry --text=Input\ a\ program\ to\ run --title=Run").read().replace('\n', ' ') 
run = os.system(str(inputRun))

```

Try that, see if it works for you.

---

### Post by -grubby on 2008-06-29
Yep, that works fine. I think it's read() that does it.

---

