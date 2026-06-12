---
title: "while sum loop"
date: 2011-11-20
forum: Programming Talk
---

### Post by crownedzero on 2011-11-20
Kind silly but I'm getting an infinite loop passing command line args to a while loop and attempting to sum them with the output shown as

var1 + var2 + var3 = sum

while -z $1 do
    echo -n "var + "
    shift
done 

kinda that fashion I can't even get them to display

---

### Post by crdlb on 2011-11-21
Is this a bash script? I guess you lost some brackets due to bbcode (please use code tags next time).

```
#!/bin/bash
while [ -n "$1" ]; do
    echo -n "$1 + "
    shift
done

```
(disclaimer: I'm not a shell expert)

-z tests for zero length; -n tests for nonzero.

FWIW, If I were making a calculator, a shell script would be my last choice.

---

### Post by gmargo on 2011-11-21
Use the shell variable **$#** to see how many arguments there are:

Here's a simple "printargs" program:
```

#!/bin/sh

while test $# -gt 0
do
    echo "$1"
    shift
done

```

---

### Post by crownedzero on 2011-11-22
You end up with 5 + 4 + 3+ = sum using this method I managed a work around its ugly but I learned something lol

---

