---
title: "I have like 5 network managers, ****!"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by RedTooth on 2008-06-15
I messed around with some commands and made myself 5 network managers in the notification area... 

How do i remove them? I know it have to do a command in terminal.

---

### Post by RedTooth on 2008-06-15
Oh yeah and the command i used by accident was : nm-applet --sm-disable &

---

### Post by durand on 2008-06-15
```
killall -9 nm-applet
```

---

### Post by RedTooth on 2008-06-15
Wow it worked, Thanks! I had 7 by the time you replied... haha

---

### Post by RedTooth on 2008-06-15
Oh wait, now how do i make one come back?

---

### Post by durand on 2008-06-15
uh, use that command you used?

---

