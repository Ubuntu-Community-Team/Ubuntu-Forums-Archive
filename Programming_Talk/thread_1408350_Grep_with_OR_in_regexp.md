---
title: "Grep with OR in regexp"
date: 2010-02-16
forum: Programming Talk
---

### Post by amsterdamharu on 2010-02-16
Sorry this might sound realy stupid but I can't get this one to work, looking for a file that is executable so send ls to grep and look for anything that starts with - then 2, 5 or 8 characters then x.
Regexp should look a like this:

^-(..x|.....x|........x)
or this
^-..x | ^-.....x | ^-........x

but can't get this into a command like

 ls -l | grep '^-..x | ^-.....x'

Looked all over the place for tutorials and man pages but no example of grep egrep or anything with a regexp that uses OR in it.

---

### Post by MinimalBin on 2010-02-16
[*Backslash*]("http://en.wikipedia.org/wiki/Backslash") should solve the *problem*.

---

### Post by amsterdamharu on 2010-02-16
Thank you. Got it now. I am always sloppy with the spaces the quotes and what not.

ls -l | grep '^-..x \| ^-.'
returns nothing.

Should be:

```
ls -l | grep '^-..x\|^d'
```

---

