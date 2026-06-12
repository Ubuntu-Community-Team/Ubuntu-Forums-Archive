---
title: "[SOLVED] Preview Icons"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Dougie187 on 2008-09-18
I have a rather odd issue happening. It just started the other day. I don't really know what happened when it started, but basically I use to have preview icons for files, such as mkv files, or pdf files. Now they are just icons, and I don't know why.

I was curious if anyone could help me get the previews back, I have looked in nautilus preferences and the properties of the files themselves, but none of them helped.

---

### Post by ace007 on 2008-09-18
I am guessing...but I think the GIMP thumbnails files for nautilus? Did you uninstall the GIMP?

EDIT: The following may not solve your problem, but it's relevant.

[http://ifireball.wordpress.com/2007/12/29/fixing-thumbnails-in-nautilus/](http://ifireball.wordpress.com/2007/12/29/fixing-thumbnails-in-nautilus/)

---

### Post by Dougie187 on 2008-09-18
Nope, gimp is there.

---

### Post by Dougie187 on 2008-09-19
If i go into ~/.thumbnails, and clear out all of the current thumbnails in there (mainly in fail, but even in all the other ones) They don't get remade. Even if I try using the nautilus script that is in the link above.

Edit:
Removing the entire ~/.thumbnails dir fixed my issue. Thanks!

---

