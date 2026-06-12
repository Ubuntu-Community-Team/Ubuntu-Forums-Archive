---
title: "Python converting &amp;#number;"
date: 2009-07-02
forum: Programming Talk
---

### Post by NoBugs! on 2009-07-02
I was curious, is there a way for a python program to convert an input string like this:
"&#38;#126;"
to this?:
"~"

---

### Post by .Maleficus. on 2009-07-02
chr(126)

Remove the &# and enter the ASCII number for the character you want.

[http://docs.python.org/library/functions.html#chr](http://docs.python.org/library/functions.html#chr)

---

### Post by NoBugs! on 2009-07-02
It seems there's no quick shortcut to change &amp;lt; or &amp;#60; to < ?
or convert &amp;cent; or &amp;#162; to ¢ ?

Or would html parser be appropriate for this?

---

### Post by smartbei on 2009-07-02
Had a look around - check out the module htmlentitydefs.

Specifically, htmlentitydefs.name2codepoint.

---

### Post by NoBugs! on 2009-07-02
Thanks. I think I found a good example of that here:
[http://bytes.com/groups/python/555936-unescape-html-entities](http://bytes.com/groups/python/555936-unescape-html-entities)

---

