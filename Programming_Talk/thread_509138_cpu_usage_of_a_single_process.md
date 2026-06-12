---
title: "cpu usage of a single process"
date: 2007-07-25
forum: Programming Talk
---

### Post by kits123 on 2007-07-25
i'm new to shell scripting.
i somehow managed to get the cpu usage and mem usage of any given pid.:KS
with this:

```
ps aux | grep $pid | awk '{print "% CPU usage of", $2 " is: ", $3}' | grep $pid
ps aux | grep $pid | awk '{print "% MEM usage of", $2 " is: ", $4}' | grep $pid
```

now i want to use C code to get a single  process (when the pid is given as input) cpu usage in linux.
i tried on windows and got it.but then getprocesstimes() APIs are OS specific.

can i get a code in c so that i can run it properly in linux?i have tried so many things and now i'm drained.:(:confused:

thanks in advance

---

### Post by nichipet on 2007-07-25
I don't know C very well, but I can suggest that you give us the code that worked in Windows, so we have a starting point to look at.

---

### Post by meatpan on 2007-07-25
Take a look at the function 'getrusage'.  You can find it in the header "sys/resource.h"

I'm pretty sure this function is applicable to a vanilla ubuntu install.

---

