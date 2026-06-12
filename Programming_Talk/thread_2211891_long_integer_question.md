---
title: "long integer question"
date: 2014-03-18
forum: Programming Talk
---

### Post by wingnut2626 on 2014-03-18
Lets say I have:    long max_data, max_rows;How does this work?  (If you need more of the code im looking at, please let me know.)    max_data = (argc >= 4) ? strtol(argv[3], NULL, 10) : 512;    max_rows = (argc >= 5) ? strtol(argv[4], NULL, 10) : 100;

---

### Post by ofnuts on 2014-03-18
You gave a ternary operator (?:) that evaluates a condition (argc >= 4), and if true return the item before the semicolon (strtol(argv[3], NULL, 10)) or otherwise returns the second item (512). So if you gave at least 4 arguments (so argv[3] exists) then it returns the conversion of the string in argv[3] to a long integer, interpreting it as a base 10 number. In other words this is shorthand for
```

long max_data;
if (argc >= 4) {
    max_data=strtol(argv[3], NULL, 10)
} else {
       max_data = 512
}

```

Or slightly better IMHO:

```

long max_data=512; // default value made more visible and unmissable
if (argc >= 4) {
    max_data=strtol(argv[3], NULL, 10)
} 

```

---

