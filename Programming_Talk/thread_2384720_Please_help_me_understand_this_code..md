---
title: "Please help me understand this code."
date: 2018-02-11
forum: Programming Talk
---

### Post by mak. on 2018-02-11
Code:
```
#!/bin/bash

for var1 in 1 2 3
do
   for var2 in 0 5
   do
      if [ $var1 -eq 2 -a $var2 -eq 0 ]
      then
         break 2
      else
         echo "$var1 $var2"
      fi
   done
done
```

Output: 1 0
1 5


I am not understanding the logic of this code really well. Why is the output like that? Please explain.

---

### Post by steeldriver on 2018-02-11
Perhaps it would help you to understand if you enumerate the loop values?

```

var1      var2
----      ----
1          0
1          5
2          0         <- at this point [ $var1 -eq 2 -a $var2 -eq 0 ] is TRUE so the break is executed
2          5
3          0
3          5

```

The break exits from both the inner and outer loop:

```

$ help break
break: break [n]
    Exit for, while, or until loops.

    Exit a FOR, WHILE or UNTIL loop.  [COLOR=#0000ff]If N is specified, break N enclosing
    loops.[/COLOR]

    Exit Status:
    The exit status is 0 unless N is not greater than or equal to 1.

```

---

### Post by mak. on 2018-02-11
I understood now. Thanks a lot.

---

