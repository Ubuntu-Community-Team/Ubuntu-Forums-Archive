---
title: "executable file that changes my resolution"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by taikonaut on 2008-05-07
Hi everybody,

I use an external Display(Samsung SyncMaster 226bw) on my Notebook(MSI s260, 12") and each time I reboot the resolution is at 1280*800 instead of 1680*1050. I always need to change the resolution manually.

Can anybody help me to create a file which changes the resolution? This would give me the possibility to easily change the resolution when I'm running my external Display.

Regards,
Taiko

---

### Post by bluefrog on 2008-05-07
create a script which will be launched upon logging of your user.

vi myres.sh
```
#!/bin/bash
xrandr -s 1680x1050
```

chmod u+x myres.sh

open system/pref/session and include myres.sh in the program to be launched upon logging

---

### Post by taikonaut on 2008-05-08
Works great!!! ThankS! :guitar:

---

