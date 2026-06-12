---
title: "Replace first occurence of a string in a file"
date: 2009-07-20
forum: Programming Talk
---

### Post by apoth on 2009-07-20
I've tried looking at awk and sed for this, but hours of googling hasn't helped!

I'd like to do a s/foo/bar/ for only the first instance of foo in a file. Not the first occurrence per line, not on line n, but the first occurrence wherever it may be in a file.

Any suggestions? Thanks.

---

### Post by stroyan on 2009-07-20
With sed you could use a range to limit where the substitution is done.  This says to make the change in all lines from the first line to the first line that matches the pattern.
```

sed '0,/pattern/s/pattern/replacement/'

```

With awk you could use a variable to remember to suppress additional substitutions.
```

awk '/pattern/{if (M==""){sub("pattern","replacement");M=1}}{print}'

```

---

### Post by apoth on 2009-07-21
> **stroyan said:**
> ```

sed '0,/pattern/s/pattern/replacement/'

```

Thanks, I'd seen that before and tried:

```
sed '0,s/foo/bar/'
```

I'm not sure if I've interpreted something wrong but it results in this error:

sed: -e expression #1, char 3: unexpected `,'

> **stroyan said:**
> ```

awk '/pattern/{if (M==""){sub("pattern","replacement");M=1}}{print}'

```

This one works a treat though, thanks! :)

---

### Post by apoth on 2009-07-21
I'm trying to pass a parameter into a script to exploit this:

```
#!/bin/bash
LEVEL=$1
function replace()
{
        awk '/TRACE|DEBUG|INFO|WARN|ERROR/{
                if (M=="") {
                        sub(/TRACE|DEBUG|INFO|WARN|ERROR/, "${LEVEL}");
                        M=1;
                }
        }
        {
                print;
        }' ${JB_HOME}/server/${USER}/conf/log4j.xml
}

replace
```

but the string ${LEVEL} is replaced into the match, rather than its value. Any ideas? Thanks.

---

### Post by ghostdog74 on 2009-07-21
use awk's -v option to pass variable from shell to awk
```

LEVEL=....
function ...{
   awk -v level=$LEVEL '{
         ..........
   }'
}

```

---

### Post by apoth on 2009-07-21
Ah, all finally working. Thanks a lot! :)

---

### Post by stroyan on 2009-07-21
> **apoth said:**
> Thanks, I'd seen that before and tried:

```
sed '0,s/foo/bar/'
```

I'm not sure if I've interpreted something wrong but it results in this error:

sed: -e expression #1, char 3: unexpected `,'

You are missing the second half of the range expression. Use
```

sed '0,/foo/s/foo/bar/'

```

---

