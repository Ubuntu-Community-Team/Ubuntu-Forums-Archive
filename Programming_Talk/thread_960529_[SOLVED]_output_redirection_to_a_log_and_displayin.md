---
title: "[SOLVED] output redirection to a log and displaying the results"
date: 2008-10-27
forum: Programming Talk
---

### Post by cybo on 2008-10-27
i need to be able to redirect my output to a log and display the output at the same time. something like:

shell> command >& logfile.log | tee logfile.log

I get errors if i do it this way. 

does anyone know how to do it?

thnx

---

### Post by ssam on 2008-10-27
do you just need to do
```

command  | tee logfile.log

```

---

### Post by cybo on 2008-10-27
Not exactly. I need to be able to log stderr and stdout. tee will log only stdout. but i think i figured it out. if you use
command |& tee logfile.log. it should work.

---

