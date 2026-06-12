---
title: "first awk script"
date: 2011-01-17
forum: Programming Talk
---

### Post by aliyanage on 2011-01-17
Hi all,

I am totally new to awk scripting but found it very very useful in the past. So far I've only used it on the command line for simple search tasks.

I now would like to write a script which searches a messaging logfile. I want the script to output the first successful message and the last successful that was sent out.

Does anyone have any example scripts that would help me to accomplish this?


Regards,
aliyanage

---

### Post by DaithiF on 2011-01-17
this may get you started:
```
awk '/success/ { if(!first) first=$0; last=$0 } END { print first; print last }' /path/to/file
```

---

### Post by ghostdog74 on 2011-01-17
```

 awk '/success/&&!f{v=$0;f=1}/success/{last=$0}END{print v;print last}' file

```

---

