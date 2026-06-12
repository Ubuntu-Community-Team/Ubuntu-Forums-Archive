---
title: "Can someone help me implement this patch?"
date: 2008-08-27
forum: Packaging and Compiling Programs
---

### Post by xl_cheese on 2008-08-27
Comment #7 has an attachment of a patch that I'd like to try out.

I can't seem to figure out how to get the thing patched in.

[http://bugzilla.gnome.org/show_bug.cgi?id=500437](http://bugzilla.gnome.org/show_bug.cgi?id=500437)

---

### Post by Oldsoldier2003 on 2008-08-27
Moved from tutorials and tips moderation queue. This is a support request

---

### Post by Oldsoldier2003 on 2008-08-27
> **xl_cheese said:**
> Comment #7 has an attachment of a patch that I'd like to try out.

I can't seem to figure out how to get the thing patched in.

[http://bugzilla.gnome.org/show_bug.cgi?id=500437](http://bugzilla.gnome.org/show_bug.cgi?id=500437)

quick answer:
download the source and then patch it. 
```
cd /directory/with/source/code
patch -p0 < /path/to/patch
```

then compile the source and install it.

if you have more questions this is the place to get help- just let folks know exactly what you did and paste the error messages.

---

