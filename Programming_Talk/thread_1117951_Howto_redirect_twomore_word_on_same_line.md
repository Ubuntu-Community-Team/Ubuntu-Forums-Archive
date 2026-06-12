---
title: "Howto redirect two/more word on same line"
date: 2009-04-06
forum: Programming Talk
---

### Post by aliahsan81 on 2009-04-06
HI

Is that possible that output of two command can redirected to one line like.


```

echo "its me" >> test.txt
echo "  my name " >> test.txt

```

i want link this 

text.txt content

its me  my name

Possible let me know

---

### Post by dwhitney67 on 2009-04-06
```

echo -n "it's me"
echo " my name"

```
Note the -n option.  It indicates that a newline should NOT be outputted.

---

### Post by aliahsan81 on 2009-04-06
actually i was using cat also.possible with

---

### Post by ghostdog74 on 2009-04-06
use printf instead of echo.

---

