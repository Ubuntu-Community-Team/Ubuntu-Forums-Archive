---
title: "awk test script fails to print variables"
date: 2015-01-31
forum: Programming Talk
---

### Post by matt174 on 2015-01-31
In learning to use awk, I came across this example script, and copy-pasted to a txt file to test it out:

```
#!/bin/awk -f

     BEGIN {

    for (i=1; i <= 10; i++) {
        printf "The square of ", i, " is ", i*i;
    }

exit;
}


```

But I get this from cli:

```
matias@...:gradebooks$ awk -f printsquares.awk
The square of The square of The square of The square of The square of The square of The square of The square of The square of The square of


```

---

### Post by steeldriver on 2015-01-31
awk's 'printf' expects a C-style format string followed by arguments 

```

        printf "The square of %d is %d\n", i, i*i;

```

or just change 'printf' to the simpler 'print'

---

### Post by Bucky Ball on 2015-01-31
*Thread moved to **Programming Talk**.*

---

### Post by 3246251196 on 2015-02-01
If you are using the hashbang (which for me is /usr/bin/awk) you should just be able to execute the file directly (having made it executable) as in:

```

$ ./printsquares.awk

```

---

### Post by matt174 on 2015-02-02
Problems solved! Thanks, guys.

---

### Post by Bucky Ball on 2015-02-02
Good news. Please mark thread as solved to help future travelers. See the second link in my signature for how. Thanks.

---

