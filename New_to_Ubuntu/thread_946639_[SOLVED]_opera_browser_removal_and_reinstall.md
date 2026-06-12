---
title: "[SOLVED] opera browser removal and reinstall"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by workshop1702 on 2008-10-13
hi had problems with opera , so removed it using add remove then reinstalled it but something is wrong as it wont open , maybe i didnt remove everything , anyone any ideas please

---

### Post by jbrown96 on 2008-10-13
Try using Synaptic (System-->Admin-->Synaptic) to Completely Remove (rather than the normal uninstall) it. That should remove everthing. Then reinstall

---

### Post by SunnyRabbiera on 2008-10-13
also hit control-h to unhide the hidden opera directory so you can delete it

---

### Post by aysiu on 2008-10-13
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and post the output back here? ```
dpkg -s opera
ls -l ~/.opera
opera &
```

---

### Post by workshop1702 on 2008-10-13
deleating the hidden opera files did the trick , thanks this problem is now solved

---

