---
title: "Printing consecutevely in a same line"
date: 2007-12-22
forum: Programming Talk
---

### Post by tashe on 2007-12-22
How can I make this happen in a BASH script?
1 2 3 4 5
* * * *
1 2 3
* *
1
* *
1 2 3
* * * *
1 2 3 4 5

I know the basic idea (with a for loop), but I'm confused how can i make the thing to print the number or he * in a row. Can anybody give me a clue?
thanks

---

### Post by duff on 2007-12-22
edit..missread nevermind

---

### Post by Bachstelze on 2007-12-22
something like :

```
firas@Nobue ~ % for i in 1 2; do echo -n "$i "; done; echo ""
1 2

```

(the -n swich to echo tells it not to add a newline character at the end)

---

### Post by tashe on 2007-12-22
sweet :)
thank you

---

### Post by ghostdog74 on 2007-12-22
```

printf "%s " {1..5}

```

---

