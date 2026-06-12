---
title: "[SOLVED] Finding a specific process in console."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by kajman on 2008-11-26
If I want to kill a process, but it isn't shown in the top command, how can I find it pid, assuming that I know its name?

I tried to use ps command (in console after pressing Ctrl+Alt+F1) but it has shown only 3 processes and I was helpless, as it was not there.

I tried to sort the columns from top, but it wasn't there also, and I cannot always count that I find the process that way.

---

### Post by taurus on 2008-11-26
You need to include -a for all processes.

```
ps -A
```

---

### Post by kajman on 2008-11-26
Thanks, now I see that my question shouldn't have been asked in the first place. Need to read the man pages more often. Sorry about that, and thanks again for a quick reply.

---

### Post by binbash on 2008-11-26
sample : 

ps aux | grep firefox

or you can play with ps aux

---

