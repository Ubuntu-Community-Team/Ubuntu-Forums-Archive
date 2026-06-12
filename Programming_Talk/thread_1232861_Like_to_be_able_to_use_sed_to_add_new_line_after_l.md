---
title: "Like to be able to use sed to add new line after line match"
date: 2009-08-06
forum: Programming Talk
---

### Post by Gen2ly on 2009-08-06
Been looking around for this but haven't been able to find anything.

I'd like to be able to add a new line after matching text in a line.

For example, say I got:

```
#output databases: mysql, snort, password yourpassword, more, blah
```

and after this line I'd like to add:

```
#output databases: mysql, snort, password yourpassword, more, blah
darn right
```

So far I got:

```
sed -i -e 's`^#output database$`#out$ \
darn right`g' file
```

As you can see I'm at a loss as what the second value should be.  I'd like to be able to match this generically.  Is this possible?  Also does the first value (^output database$) appear right?

---

### Post by Gen2ly on 2009-08-06
Ah i got it (Gentoo [Developer's guides]("http://devmanual.gentoo.org/tools-reference/sed/index.html") are awesome):

```
sed -i -e `^text to match$/a text to add on new line` file
```

Gotta like sed, Doh!

---

### Post by da_steve123 on 2012-12-03
Thanks :D
Btw heads up, the forwardslash has been removed in the above but the link is good :D

---

