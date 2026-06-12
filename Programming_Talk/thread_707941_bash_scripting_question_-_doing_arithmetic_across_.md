---
title: "bash scripting question - doing arithmetic across lines"
date: 2008-02-25
forum: Programming Talk
---

### Post by pytheas22 on 2008-02-25
I'm sorry to be asking a question about simple bash scripting, but I'm new to it and I've been working on this for a long time without any progress.

I have a file that looks like this:
```

2       goat
2       dog
1       sheep
1       pig
1       cat
1       cat
1       bird
3       goat
1       sheep
1       dog
```

I want to write a script that will look at the second field of each line, and if it matches $2 of another line anywhere else in the file, then both lines will be replaced by a single line in which $1 equals the sum of the first fields of the two original lines.  In other words, the output should look like:
```

5       goat
3       dog
2       sheep
2       cat
1       bird
1       pig
```

I've tried using gawk and uniq but can't figure out how to put them together properly.  Any hints would be greatly appreciated.

---

### Post by ghostdog74 on 2008-02-25
use awk's associative arrays to store the values
```

# awk '{a[$2]+=$1}END{for (i in a) print a[i],i}' file
1 pig
2 sheep
1 bird
2 cat
5 goat
3 dog

```

---

