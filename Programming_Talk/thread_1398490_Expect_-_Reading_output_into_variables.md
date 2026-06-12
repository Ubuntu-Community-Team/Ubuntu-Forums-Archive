---
title: "Expect - Reading output into variables"
date: 2010-02-04
forum: Programming Talk
---

### Post by chrisvaughanuk on 2010-02-04
Hi,

I am writing a script that spawns a telnet session. I am trying to read the output of some of the telnet session into a variable if possible. E.g. I write a command similar to:

send $COMMAND
I would then like to read telnet's response to a variable so that I can run an IF statement on the output. Can anyone help please?

---

### Post by chewearn on 2010-02-05
Something like this?
```
RETVALUE=`send $COMMAND`
```

---

