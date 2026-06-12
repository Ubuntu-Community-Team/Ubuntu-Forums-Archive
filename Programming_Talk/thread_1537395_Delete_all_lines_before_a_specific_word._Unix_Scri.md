---
title: "Delete all lines before a specific word. Unix Scripting"
date: 2010-07-23
forum: Programming Talk
---

### Post by hakermania on 2010-07-23
Let's say we have a file containing:
```
alllllsadfsdasdf
qwdDDDaassss
ccxxcxc#2222
dssSSSSddDDDD
D1Sqn2NYOHgTI
Hello
Alex
ssS@3
```

Ok, and let's say we want to delete all words from D1Sqn2NYOHgTI and back, this means
to delete the words (and the lines of them) :
```
alllllsadfsdasdf
qwdDDDaassss
ccxxcxc#2222
dssSSSSddDDDD
D1Sqn2NYOHgTI
```

---

### Post by trent.josephsen on 2010-07-23
```
$ sed -e '/D1Sqn2NYOHgTI/q'
```

'q' is a sed command that exits the script after printing the current pattern space.

---

### Post by hakermania on 2010-07-23
ok, thank you very much!

---

### Post by ghostdog74 on 2010-07-23
you said you want to delete from D1Sqn2NYOHgTI and back, so this is the sed command
```

$ cat file
alllllsadfsdasdf
qwdDDDaassss
ccxxcxc#2222
D1Sqn2NYOHgTI
dssSSSSddDDDD
Hello
Alex
ssS@3

$ sed -n '/D1Sqn2NYOHgTI/,$ { /D1Sqn2NYOHgTI/!p}' file
dssSSSSddDDDD
Hello
Alex
ssS@3


```

you can also use awk

```

$ awk '/D1Sqn2NYOHgTI/{f=1;next}f' file
dssSSSSddDDDD
Hello
Alex
ssS@3


```

---

### Post by piratesmack on 2010-07-24
Here's what I came up with
```

$ awk '/^D1Sqn2NYOHgTI$/ {print NR + 1}' afile | xargs -I {} tail -n+{} afile
Hello
Alex
ssS@3

```

:oops:

Will have to read up on sed and awk

---

