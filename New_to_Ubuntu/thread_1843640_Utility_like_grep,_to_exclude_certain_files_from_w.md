---
title: "Utility like grep, to exclude certain files from wildcard searches"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by jdgregson on 2011-09-13
Basically, I want a utility called "except". You know, for the times when you want to remove every file in a directory except those two or three? For example, something like

```

mv foo bar ../
rm -r ./*
mv ../foo ./
mv ../bar ./

```could be done a lot easier, by piping it through a utility like 

```

rm -r ./* | except foo bar

```Does anybody know of a utility like that? It would be very useful for me sometimes.

---

### Post by sisco311 on 2011-09-13
No need for a utility. In bash, you can use extended globs. See: [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

Something like:
```
shopt -s extglob
echo !(foo|bar)

```

---

### Post by jdgregson on 2011-09-13
Oh, sweet! That does exactly what I needed! Thanks! :D

---

