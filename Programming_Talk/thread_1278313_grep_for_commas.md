---
title: "grep for commas?"
date: 2009-09-29
forum: Programming Talk
---

### Post by wrathkeg on 2009-09-29
Hi all,

I have  a load of comma-separated tables.  Almost all lines have three entries, separated by commas e.g. 

```
one,two,three
```

Some lines have only two entries, and therefore one comma e.g.

```
one,two
```

I want to get rid of the lines with two entries/one comma.  It seems to me that a decent way to do this would be to use grep to find all the lines containing two commas..... But I can't figure out how to do it!  Any pointers (or even alternate solutions I could put in a shell script) would be welcome.

Thanks in advance,

wrathkeg

---

### Post by Simian Man on 2009-09-29
Pretty simple:
```
[simian@splinter ~]$ cat temp 
one,two,three
a,b
x,y,z
qwe,ter,ert
hi,there
[simian@splinter ~]$ **cat temp | grep ".*,.*,.*"**
one,two,three
x,y,z
qwe,ter,ert
[simian@splinter ~]$ 

```

---

### Post by wrathkeg on 2009-09-29
excellent! thanks.  I had been putting "*" as the wildcard instead of ".*".
best,
wrathkeg

---

