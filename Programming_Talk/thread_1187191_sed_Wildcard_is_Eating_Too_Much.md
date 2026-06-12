---
title: "sed: Wildcard is Eating Too Much"
date: 2009-06-14
forum: Programming Talk
---

### Post by Penguin Guy on 2009-06-14
I'm trying to remove all comments from a piece of code:
```
~ $ [COLOR="Red"]echo "code # comments # more comments" | sed 's_^\(.*\)#.*$_\1_
code # comments [/COLOR]
```
As you can see the first wildcard [COLOR="Green"].*[/COLOR] is eating as much text as it possibly can, all the way up to the last [COLOR="Green"]#[/COLOR]. How can I make it eat the bare minimum, only up to the first [COLOR="Green"]#[/COLOR]?
If this is not possible, then is there some way to process sed backwards so that the last wildcard gets processed first?

Two ways of solving the problem (thanks to [MadCow108]("http://ubuntuforums.org/member.php?u=804725")):
```
~ $ [COLOR="Green"]echo "code # comments # more comments" | sed 's_^\([^#]*\).*$_\1_'
code [/COLOR]
```
*or*
```
~ $ [COLOR="Green"]echo "code # comments # more comments" | perl -p -e 's/^(.*?)#.*$/\1/'
code [/COLOR]
```

---

### Post by MadCow108 on 2009-06-14
you could use this:
echo "code # comments # more comments" | sed 's_^\([^#]*\).*$_\1_'

alternativly you could use perl:
echo "code # comments # more comments" | perl -p -e 's/^(.*?)#.*$/\1/'

where .*? means non greedy matching
[http://docstore.mik.ua/orelly/perl/cookbook/ch06_16.htm](http://docstore.mik.ua/orelly/perl/cookbook/ch06_16.htm)

---

### Post by Penguin Guy on 2009-06-14
> **MadCow108 said:**
> you could use this:
echo "code # comments # more comments" | sed 's_^\([^#]*\).*$_\1_'

alternativly you could use perl:
echo "code # comments # more comments" | perl -p -e 's/^(.*?)#.*$/\1/'

where .*? means non greedy matching
[http://docstore.mik.ua/orelly/perl/cookbook/ch06_16.htm](http://docstore.mik.ua/orelly/perl/cookbook/ch06_16.htm)
Thanks, both solutions work perfectly!

---

