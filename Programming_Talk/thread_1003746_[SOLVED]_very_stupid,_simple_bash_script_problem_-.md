---
title: "[SOLVED] very stupid, simple bash script problem - for loop"
date: 2008-12-06
forum: Programming Talk
---

### Post by mcai8sh4 on 2008-12-06
Just a little question.
I've been writing bash scripts for quite a while and, whilst I always get there in the end, I usually find little things that don't work when I think they should. I usually just use another method, but his one puzzles me....

Simple example (that doesn't work):
```
MAX=20
for count in {1..$MAX}; do
     ...
done
```

why can't I put a variable in the braces?

Thanks for reading

-s

---

### Post by unutbu on 2008-12-06
[PHP]#!/bin/bash
MAX=20
for count in $(seq 1 "$MAX"); do
    echo "$count"
done
[/PHP]

---

### Post by mcai8sh4 on 2008-12-06
> **unutbu said:**
> [PHP]#!/bin/bash
MAX=20
for count in $(seq 1 "$MAX"); do
    echo "$count"
done
[/PHP]

ah, thanks for that!

---

### Post by dwhitney67 on 2008-12-06
Or:
```

MAX=20

for (( i = 0; i < $MAX; ++i ))
do
        echo -n "$i "
done
echo ""

```

---

### Post by mcai8sh4 on 2008-12-06
> **dwhitney67 said:**
> Or:
```

MAX=20

for (( i = 0; i < $MAX; ++i ))
do
        echo -n "$i "
done
echo ""

```

lol - I spent 5+ years using c (and similar) yet I've never used that method in a bash script. Thanks

---

