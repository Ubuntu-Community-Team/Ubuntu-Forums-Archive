---
title: "ipc message queue problem"
date: 2012-11-13
forum: Programming Talk
---

### Post by newman2006006 on 2012-11-13
Hello , i wrote  ipc message queue programm and good compile Success &#1548;but run file message receiver below Error:


```
msgget: No such file or directory
```

Please Help me.

---

### Post by The Cog on 2012-11-13
try this command:
```
./msgget
```

Your current directory is not part of your executable search path (unlike windows).

---

### Post by newman2006006 on 2012-11-14
Please explain more , Now what I do?

---

