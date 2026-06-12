---
title: "weirdest error ever (bash script)"
date: 2008-01-05
forum: Programming Talk
---

### Post by forcotton on 2008-01-05
I was debugging a bash script and met the weirdest error I have ever seen:
```
/bin/sleep: line 1: ELF: command not found
```
was given in response to "sleep 10m".  The error gone away next time I run it. 

I wonder what caused it. Seems like the beginning of /bin/sleep was inserted a shebang. Gee.

---

### Post by stroyan on 2008-01-05
You can get that error from```
. /bin/sleep 10m
```.  I don't know what you could have done that would cause that to occur just once.  I suppose some transient error could have caused the exec to fail and bash to try treating the file as a shell script instead of an a.out.  Perhaps a resource shortage or /bin/sleep being updated and overwritten just as you were running your script.  All temporary causes seems extremely unlikely.

---

