---
title: "executing shell commands with ruby??"
date: 2005-09-07
forum: Programming Talk
---

### Post by pranith on 2005-09-07
hi,
Is there ne module in ruby that executes linux shell commands
I tried with exec() but it terminates the program just after the exec("<linux command>") part is completed it will not execute the remaining part of the ruby program so what shud I do?? Is there a better module?? or shuld we modify exec()
anticipating help
thanks
bye
pranith

---

### Post by wtd on 2005-09-07
You can either use the "system" method to simply run the command...

```
system "ls"
```

Or you can use backticks to capture the output of the program.

```
ls_results = `ls`
```

---

### Post by pranith on 2005-09-07
thanks 
thank u very much

---

### Post by pavel989 on 2007-12-13
oh wow, like an hour of googling and its that simple? thanks very much (i love ruby!)

---

