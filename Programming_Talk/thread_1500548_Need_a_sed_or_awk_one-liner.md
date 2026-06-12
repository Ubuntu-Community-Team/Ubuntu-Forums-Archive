---
title: "Need a sed or awk one-liner"
date: 2010-06-03
forum: Programming Talk
---

### Post by DGortze380 on 2010-06-03
I can't seem to find the right syntax for this.

Using Bash with sed and/or awk I need to replace all spaces in a string with a backslash and a space.

EX.

Name With Spaces
Name\ With\ Spaces

Any help would be appreciated.

---

### Post by DaithiF on 2010-06-03
Hi,

```
$ echo "Name With Spaces" | sed 's/ /\\ /g'
Name\ With\ Spaces

```

---

### Post by DaithiF on 2010-06-03
or just using bash:
```
$ in="Names With Spaces"
$ echo ${in// /\\ }
Names\ With\ Spaces
```

---

### Post by DGortze380 on 2010-06-03
Awesome!

Thanks.

---

