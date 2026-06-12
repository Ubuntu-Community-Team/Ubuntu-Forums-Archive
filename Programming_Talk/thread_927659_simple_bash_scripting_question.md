---
title: "simple bash scripting question"
date: 2008-09-23
forum: Programming Talk
---

### Post by BXCracer on 2008-09-23
Hello.
i would like that my script would do the following.
If lets say 
```

fpc name.pas | grep compiled
```

Prints out something like 

```
17 lines compiled, 0.1 sec 
```

(it would be better if pc recognizes those number as a wild cards so that the value would be true no matter number of lines or time it compiled in.)
So if it prints out that ^^^ do the following ...

How can i implement all this stuff in bash scripting ?

BXC

---

### Post by ghostdog74 on 2008-09-23
i can't understand. just show what your desired output would be.

---

### Post by BXCracer on 2008-09-23
ok. I am trying to build a script that compiles and checks if the pascal program compiled successfully. And if so then starts it.

Desired output should be:
```
* lines compiled, * sec
```

* - using as a wildcard.
This line shows that program was compiled successfully.

---

### Post by ghostdog74 on 2008-09-23
```

fpc name.pas | awk '$1 > 0 && /compiled/ && /sec/{print "ok"}'

```

---

### Post by BXCracer on 2008-09-23
> **ghostdog74 said:**
> ```

fpc name.pas | awk '$1 > 0 && /compiled/ && /sec/{print "ok"}'

```

Thanks

---

