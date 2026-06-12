---
title: "[BASH] status bar"
date: 2008-02-26
forum: Programming Talk
---

### Post by Martje_001 on 2008-02-26
Hi,
I want to create a script, which has a 'status bar' (don't know how to exactly describe it in english). The script will be something like:
```
#!/bin/bash
echo 10%
echo 55%
echo 99%
echo 100%
```

the output is:
> 100%
get it? 55% replaces 10%, 99% replaces 55%, etc.

How do I do this?

---

### Post by ruy_lopez on 2008-02-26
```

echo -n "50%"
sleep 1
echo -en "\b\b\b"
echo "100%"

```

echo -e flag recognises backspace '\b'. echo -n suppresses newline. Sleep is just for demonstration.

---

### Post by Martje_001 on 2008-02-26
Thank you very very much!

---

### Post by Mr. C. on 2008-02-27
To deal with more generic output, where you don't have to calculate backspaces, etc., use termcap/terminfo capabilities along with **tput** to access them:
```

BeginOfLine=`tput hpa 0 el`

for i in 5 4 3 2 1 ; do
   echo -n ${BeginOfLine}Countdown $i...
   sleep 1
done

```
There's no end of stuff you can do.  For example, you might want to change text color too.

For more info, see :

```
man 5 termcap
man 5 terminfo
man tput
```

MrC

---

