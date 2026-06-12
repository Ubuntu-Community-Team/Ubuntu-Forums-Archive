---
title: "python and os.popen output problem"
date: 2010-09-07
forum: Programming Talk
---

### Post by wlourf on 2010-09-07
Hi,

When I run this command  (which can look ugly!)
```
        win1 = os.popen("xwininfo -tree -root | grep gedit | awk '{print $1}'").read()
        win1 = win1.rstrip()
        print win1, len(win1)
```the output is 
```
0x2800002 9
```So an hexa number with 9 characters, without quotes, but I can't convert the number 0x2800002 to a  long
```
    print long(win1)
ValueError: invalid literal for long() with base 10: '0x2800002'

```If I run a python console and type long(0x2800002), the output is ok : 41943042L.

So what am I missing ?

Thanks for any advice !

---

### Post by StephenF on 2010-09-07
> **wlourf said:**
> So what am I missing ?
ValueError: invalid literal for long() with base **10**: '0x2800002'

It's not base 10. Strip or leave the 0x - it doesn't matter.
```

print long("0x2800002", 16)

```

---

### Post by wlourf on 2010-09-08
thanks, it works !

---

