---
title: "Bash: Suppressing ANY output"
date: 2009-11-30
forum: Programming Talk
---

### Post by neur0 on 2009-11-30
Don't know if this is the right section, but I want to run a bash script in the background (which I can do with 'bg' or '&') but when I get my prompt back I don't want any status messages or errors (from this script) to print on the screen (why would I even want my prompt back if its constantly being littered with messages?)

---

### Post by DaithiF on 2009-11-30
have you tried redirecting stdout and stderr?
```
somescript > /dev/null 2>&1

```

---

### Post by mo.reina on 2009-11-30
> **daithif said:**
> have you tried redirecting stdout and stderr?
```
somescript > /dev/null 2>&1

```

+1

---

### Post by neur0 on 2009-11-30
Ok, that worked after 'CTRL-z' and 'bg' since it didn't give me back the prompt. I guess I was trying something like 

somescript & > /dev/null 2>&1

Basically a one-liner
But this did the job.
Thanks

---

