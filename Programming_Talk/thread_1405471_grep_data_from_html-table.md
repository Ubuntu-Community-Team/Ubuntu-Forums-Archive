---
title: "grep data from html-table"
date: 2010-02-12
forum: Programming Talk
---

### Post by frankbooth on 2010-02-12
I'm new to Bash so I've been stuck with this problem for a while now.
What I'm trying to do:

Inside a .txt (with html code) there's data I want to grep, more specifically inside a table, like this:

```
<table width="560" border=0><th>Datum</th><th>Trafik in</th><th>Trafik ut</th><th>Total trafik</th><tr><td>2010-02-12</td><td>333.29 MB</td><td>267.72 MB</td><td>601.01 MB</td></tr>
```*[SIZE=1](above code can be found on row 30 inside the .txt)[/SIZE]*

What I want to grep is inside the first table row and forth table cell (in this case '601.01 MB' would be the data I'd want to grep).

Anyone got any ideas?

---

### Post by sanderj on 2010-02-12
What else is there in the file?

My first, utterly ugly attempt:

```
sander@quirinius:~$ cat troep.txt 
blabla
blabla
<table width="560" border=0><th>Datum</th><th>Trafik in</th><th>Trafik ut</th><th>Total trafik</th><tr><td>2010-02-12</td><td>333.29 MB</td><td>267.72 MB</td><td>601.01 MB</td></tr>
blabla
blabla

sander@quirinius:~$ cat troep.txt | grep -i table | head -1 | awk -F\> '{ print $18 }' | awk -F\< '{ print $1 }'
601.01 MB
sander@quirinius:~$ 
```

---

### Post by diesch on 2010-02-12
```
awk -F '.*<td>|</td></tr>' '/<table width="560" border=0>/ {print $2}' test.txt
```

Adapt the */<table width="560" border=0>/ *to whatever you need to get the right line.

---

