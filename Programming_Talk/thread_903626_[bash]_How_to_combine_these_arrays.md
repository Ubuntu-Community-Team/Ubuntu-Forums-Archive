---
title: "[bash] How to combine these arrays?"
date: 2008-08-28
forum: Programming Talk
---

### Post by bttb on 2008-08-28
Hi all,

I have two arrays in my script which turned out to be quite handy. The first holds variable names, the second options:

```
array[0]=THREADS  OPTION[0]=4
array[1]=COLOR    OPTION[1]=GREEN
array[2]=BOLDFACE OPTION[2]=YES
...               ...

```

I'd like to go from there to here:

```
THREADS=4
COLOR=GREEN
BOLDFACE=YES
...

$ echo $COLOR
GREEN
```

Anybody knows how to achieve this without using eval (${!VAR} is fine)?

Kind regards!

---

### Post by humberto.cruz on 2008-08-28
why can't you use eval ?

c=0;while [ $c -lt ${#names[@]} ]; do eval ${names[$c]}=${options[$c]};c=$((c+1)); done

[]s
Humberto

---

### Post by bttb on 2008-08-30
This works:

```

#!/bin/bash

array[0]=THREADS
array[1]=COLOR
array[2]=BOLDFACE

OPTION[0]=4
OPTION[1]=GREEN
OPTION[2]=YES

for i in 0 1 2; do
        declare ${array[i]}=${OPTION[i]}
done

echo \$COLOR = $COLOR
echo \$THREADS = $THREADS
echo \$BOLDFACE = $BOLDFACE

exit

```

---

