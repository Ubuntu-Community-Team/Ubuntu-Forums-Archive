---
title: "remove until doubled char"
date: 2011-10-17
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2011-10-17
lets say i have something like

```
/etc//var/run/motd
```how do i remove the ```
/etc/
``` and leave only ```
/var/run/motd
```I am finding symlink target and I need the absolute path, this is almost what i want but can't rid of the directory before //

the command what i using
find $DIR -maxdepth $DEPTH -type l -printf %h/%l\\n 2>/dev/null

thanks for your help

btw, I cant use readlink -f nor stat

EDIT: I am using bash as my shell

---

### Post by Vaphell on 2011-10-17
not really getting it, why don't you drop the %h/ from printf, which is what puts /etc/ there in the results in the first place?
but if you really need to have it your way and process find output
```
find <whatever> | sed 's:^.*//:/:'
```

---

### Post by Arndt on 2011-10-17
> **Vaphell said:**
> not really getting it, why don't you drop the %h/ from printf, which is what puts /etc/ there in the results in the first place?
but if you really need to have it your way and process find output
```
find <whatever> | sed 's:^.*//:/:'
```

Probably in order to handle relative symlinks.

Note that the symlink text may contain double slashes itself - then the above substitution will do the wrong thing. I suggest splitting the handling of the symlink into two cases: with and without a leading slash.

---

### Post by Mr.Pytagoras on 2011-10-17
> **Vaphell said:**
> not really getting it, why don't you drop the  %h/ from printf, which is what puts /etc/ there in the results in the  first place?
but if you really need to have it your way and process find output
```
find <whatever> | sed 's:^.*//:/:'
```

thanks, this is what i needed

> **Arndt said:**
> Probably in order to handle relative symlinks.

Note that the symlink text may contain double slashes itself - then the  above substitution will do the wrong thing. I suggest splitting the  handling of the symlink into two cases: with and without a leading  slash.

True, it is because the relative symlinks
I was also thinking about splitting it into two cases  but it would require launching find twice and i wanted to avoid that. Anyway thanks.

Just out of curiosity, is there a way how to do this without sed or splitting it into two cases?

---

