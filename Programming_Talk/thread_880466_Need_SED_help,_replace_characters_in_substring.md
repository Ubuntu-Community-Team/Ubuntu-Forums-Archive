---
title: "Need SED help, replace characters in substring"
date: 2008-08-05
forum: Programming Talk
---

### Post by limemonkey on 2008-08-05
Hi all,

i have a serious problem which i weren't able to solve with google :confused: It's a collection of source code files in which (with find and -exec) i want to replace all _ with -, but only in the following string:

```
LanguageUtil.get(pageContext, "there_are_no_events_to_show")
```
to
```
LanguageUtil.get(pageContext, "there-are-no-events-to-show")
```

Of course other underlines in the files should be untouched, so no 's/_/-/g' is not a valid answer. I came this far:
```
s/LanguageUtil\.get(pageContext, "\([a-z_]*\)")/\1/g
```
which basically finds the string which i want to replace... so basically i'm stuck at the beginning.

Any help or a suitable tutorial link is appreciated!

---

### Post by mssever on 2008-08-05
what about ```
egrep 'LanguageUtil\.get(pageContext, "\([a-z_]*\)")' | tr -- _ -
```

---

### Post by limemonkey on 2008-08-05
Sorry, i was not clear enough in my first post... :(

I want to replace all _ to - only in that function, in 1000+ source code files, in-place, this is the command i will use:

```
find /my/dir -type f -exec sed -i "" -e 's/_/-/g' {} \;
```

BUT not globally like the example ^^^above, only in the specific function i wrote in the first post.

---

### Post by ghostdog74 on 2008-08-05
try this
```

find /my/dir -type f -exec sed -i '/LanguageUtil.get(pageContext/s/_/-/g'

```

---

### Post by limemonkey on 2008-08-05
> **ghostdog74 said:**
> try this
```

find /my/dir -type f -exec sed -i '/LanguageUtil.get(pageContext/s/_/-/g'

```

Thanks, that's nearly what i want but there's too many lines like this:

```
Some.function("dont_touch"); X=LanguageUtil.get(pageContext, "yes_touch");
```

:-(

---

### Post by ghostdog74 on 2008-08-05
so you only want to change lines that starts with LanguageUtil.get??
then put a ^ 
eg
sed '/^LanguageUtil.get....'

---

### Post by limemonkey on 2008-08-05
Thanks, this is what i needed: 

```
/LanguageUtil.get(pageContext/ {;h;s/.*get(pageContext, "\([a-zA-Z_-]*\)").*/\1/g;s/_/-/g;G;s/\(.*\)\n\(.*pageContext, "\)[a-z_]*\(.*\)/\2\1\3/g;}
```

Don't laugh, i did that myself :)

I wanted to replace _ in any LanguageUtil occurence with -, no matter if there's any other code around it (which also may contain _ and which should be left untouched)

On a Mac version of sed this is what i used to go through all code:

```
find . -type f -exec sed -i "" -e '/LanguageUtil.get(pageContext, "/ {;h;s/.*get(pageContext, "\([a-zA-Z_-]*\)").*/\1/g;s/_/-/g;G;s/\(.*\)\n\(.*pageContext, "\)[a-z_]*\(.*\)/\2\1\3/g;}' {} \;
```

---

### Post by ghostdog74 on 2008-08-05
that's good, however, it could be simpler and more readable. :)

---

