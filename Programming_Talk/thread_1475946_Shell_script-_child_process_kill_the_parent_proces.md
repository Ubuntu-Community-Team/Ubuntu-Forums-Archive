---
title: "Shell script- child process kill the parent process"
date: 2010-05-07
forum: Programming Talk
---

### Post by jessy21 on 2010-05-07
Hello everyone, 

I'm trying to write a script, i would like to say the child process will kill the parent process

how would i do that?

Thanx,

---

### Post by Portmanteaufu on 2010-05-07
Assuming you wanted it in Bash, here you go:

```

#!/bin/bash
kill -9 $PPID

```
I'm pretty curious as to what you'd use this for. :)

---

