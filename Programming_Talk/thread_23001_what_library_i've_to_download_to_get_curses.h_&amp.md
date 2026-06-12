---
title: "what library i've to download to get curses.h &amp; term.h ?"
date: 2005-03-30
forum: Programming Talk
---

### Post by lorap on 2005-03-30
thanks.
pavel

---

### Post by darrenadams on 2005-03-30
A quick run of dpkg-query --search curses.h produces the following

```
$ dpkg-query --search curses.h

slang1-dev: /usr/include/slcurses.h
python2.4-dev: /usr/include/python2.4/py_curses.h
python2.4-doc: /usr/share/doc/python2.4/html/lib/module-curses.html
libncurses5-dev: /usr/include/ncurses.h
phpdoc: /usr/share/doc/phpdoc/html/ref.ncurses.html
**libncurses5-dev: /usr/include/curses.h**
```

As you can see, libncurses5-dev contains the file curses.h. As it happens, term.h is also part of the libncurses5-dev package (I checked)

---

### Post by lorap on 2005-03-30
thanks friend!
i'll check it tomorrow,gotta go sleep,falling atired:-)
thanks again.
pavel

---

