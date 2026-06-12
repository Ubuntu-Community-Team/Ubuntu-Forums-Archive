---
title: "[SOLVED] command to start a virtualbox guest"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-09-21
so i have last question about virtualbox and everything will be setup pro

i want make a launcher on AWN that will open a virtuabox guest session

i dont want the virtualbox manager thing to come up at all
(only the actual virtual windows xp and thats it)

so what would i use for a command?

i know i have seen it previously somewhere but i cant find it anywhere

---

### Post by howefield on 2008-09-21
```
VBoxManage startvm WindowsXP
```

Did you get this to work ? subsitute WindowsXP with the name of your .vdi or its UUID number.

---

### Post by tjwoosta on 2008-09-21
awesome

it works perfectly, thanks

---

### Post by howefield on 2008-09-21
Great, glad to hear it. :guitar:

---

