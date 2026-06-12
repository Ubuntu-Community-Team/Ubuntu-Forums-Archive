---
title: "Strange Behavoir with echo and awk."
date: 2009-11-08
forum: Programming Talk
---

### Post by Xqtftqx on 2009-11-08
Alright, i was doing a little script, and i needed to convert hex to ascii. i did it with: echo -e "\x41" | awk '{printf "%c\n", $1}'

But when i pass echo a variable of 2A, it prints a directory list.

try it yourself:
```

hex=2A
text=`echo -e "\x$hex" | awk '{printf "%c\n", $1}'`
echo $text

```

Example:
```

xqtftqx@Xqtftqx-Laptop:~$ cat weird.sh 
hex=2A
text=`echo -e "\x$hex" | awk '{printf "%c\n", $1}'`
echo $text
xqtftqx@Xqtftqx-Laptop:~$ ./weird.sh 
Desktop Documents Downloads index.php~ mp32aac.sh~ Music new file~ Pictures Projects Templates test~ Videos weird.sh

```

Setting $hex to anything else works fine

---

### Post by diesch on 2009-11-08
ASCII 2Ah is "*" and that gets expanded, like echo *.

Use
 ```
echo "$text"
``` instead

---

