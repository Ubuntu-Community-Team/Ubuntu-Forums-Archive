---
title: "[SOLVED] 3rd party sources include. . .?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by pHreaksYcle on 2008-11-07
What should the list of sources be in the 3rd party tab of the sources GUI?

I effed it up :(

Thanks for your responses!

---

### Post by jpeddicord on 2008-11-07
Depends on what you wanted to put in there. It typically has:
```
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner
```on a default install. Everything else is added by yourself.


Mine looks like this, but I have some extra repositories enabled, some experimental.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=90691&d=1225595041[/IMG]

---

### Post by pHreaksYcle on 2008-11-07
Appreciated, > deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner was what I was missing.

Nice avatar btw.

---

