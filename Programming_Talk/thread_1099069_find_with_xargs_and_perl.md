---
title: "find with xargs and perl"
date: 2009-03-17
forum: Programming Talk
---

### Post by dpbevin on 2009-03-17
I'm trying to convert the line endings in files that end in ',v' from *nix (\n) to windows style (\r\n).

Some of the files contain spaces or '~' and it's causing me problems.

Here's the original command I started with.

find . -type f -name '*,v' -or -name '.*,v' -print -exec perl -p -i -e 's/\n/\r\n/' {} \;

I know I should be using -print0 with find and "xargs -0" instead of -exec but I can't get it to work.

I think I'm having problems because the search/replace term in the perl script contains newlines.

Any ideas?

Thanks in advance.

David

---

### Post by ghostdog74 on 2009-03-17
making it simpler, use a while read loop
```

find ...... | while read FILE
do
 perl ......
done

```
remember to quote your variables

---

### Post by slavik on 2009-03-17
```
find `pwd` -name "*,v" -exec unix2dos {} \;
```

you might need the tofrodos package :)

---

### Post by ghostdog74 on 2009-03-17
if all your files are in 1 directory
```

# unix2dos *.v

```

---

