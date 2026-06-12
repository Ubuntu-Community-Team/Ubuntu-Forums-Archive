---
title: "Using sed/awk to display CPU/MEM% with top"
date: 2008-07-26
forum: Programming Talk
---

### Post by schauerlich on 2008-07-26
I want to use sed/awk to parse the output of top to display just the total CPU and memory %, but I have no clue how to use sed/awk and the man pages weren't very useful... any bash gurus out there?

---

### Post by ghostdog74 on 2008-07-26
you can look at the top info or man page on options that can allow you to select which fields you want to view. Also to get just the total CPU/mem (the top first few lines) 
```

top -n 1 | awk  'BEGIN{FS="[:,]"}NR==3||NR==4{print $2}'

```

---

