---
title: "Write current line from sed"
date: 2010-07-06
forum: Programming Talk
---

### Post by yc2 on 2010-07-06
In this example I try to write ("export") every line that has the string "kalle" in it.

Input file = "tbd"
Output file = "slask2"

If i do this:
$ cat tbd | sed '/kalle/w slask2'; cat slask2
I will receive the entire file before the correct lines are written


If i do this:
$ cat tbd | sed '/kalle/.w slask2'; cat slask2
I get an error message meaning that "." is unknown command (though output is correct!!)
sed: -e uttryck #1, tecken 8: okänt kommando: "."

Please give me a command that writes only the lines that contain a certain string without error messages, thanks.

/yc2 :D




```
$ cat tbd
kalle
nisse
kalle
vera
olga
kalle
nisse
oskar
oskar kalle
nisse kalle oskar
vera olle PELLE
PELLE kalle vera

$ cat tbd | sed '/kalle/w slask2'; cat slask2
kalle
nisse
kalle
vera
olga
kalle
nisse
oskar
oskar kalle
nisse kalle oskar
vera olle PELLE
PELLE kalle vera

kalle
kalle
kalle
oskar kalle
nisse kalle oskar
PELLE kalle vera
$ cat tbd | sed '/kalle/.w slask2'; cat slask2
sed: -e uttryck #1, tecken 8: okänt kommando: "."
kalle
kalle
kalle
oskar kalle
nisse kalle oskar
PELLE kalle vera

```

---

### Post by dethorpe on 2010-07-06
try the -n option on sed, it surpresses default output so lines shouldn't be written to stdout.

Craig

---

### Post by yc2 on 2010-07-06
Thanks Craig for good and quick help.

That did it.

/ycc

---

