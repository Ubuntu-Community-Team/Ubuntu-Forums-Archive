---
title: "Why doesn't this short bash script work?"
date: 2010-06-17
forum: Programming Talk
---

### Post by Zorgoth on 2010-06-17
I wrote a bash script to try to produce a parsable list of .m files in a directory with spaces in the folder names:

```

zombie=`find -name '*.m';`
for zombieface in "$zombie"; 
initstr=${initstr}${zombie}; 
if [ "`expr "$zombieface" : '.*\(..\)'`" == ".m" ]; then 
   echo \""$initstr"\"; initstr=""; fi; 
done

```

Unfortunately, for some reason my quotes get messed up; They only appear on the first and last lines, like so:

```

"./potatoes are delicious.m
./zucchinis are sickening/grapes are not.m
...
./chop down the tallest tree in the forest with a herring.m" 

```

Any explanation for this?

---

### Post by dwhitney67 on 2010-06-17
I can only assume that this version of your script produces the correct output you desire; you did not indicate what output you were hoping to obtain.
```

#!/bin/bash

find . -name '*.m' | while read zombieface
do
        initstr=${initstr}${zombieface}

        if [ "`expr "$zombieface" : '.*\(..\)'`" == ".m" ]
        then
                echo \"$initstr\"
                initstr=""
        fi
done

```

Btw, note that I inserted newlines where I thought the code needed it.  If the 'Return' key on your keyboard is broken, you should consider investing in a new keyboard.

---

### Post by Zorgoth on 2010-06-17
I want quotes around each line.

---

### Post by Penguin Guy on 2010-06-17
```
ifs='
'
```

---

### Post by dwhitney67 on 2010-06-17
> **Zorgoth said:**
> I want quotes around each line.

see my latest code update.

---

### Post by Zorgoth on 2010-06-17
Thanks!  I got a script to work to, but I have another problem now... (for another thread)

---

