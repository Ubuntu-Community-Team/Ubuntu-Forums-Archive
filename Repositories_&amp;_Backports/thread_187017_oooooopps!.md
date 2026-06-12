---
title: "oooooopps!"
date: 2006-06-02
forum: Repositories &amp; Backports
---

### Post by Caligula on 2006-06-02
that's not how it was supposed to happen... :-D 

I added the debian testing repository to my sources.list(don't ask!;) ), but unfortunately it broke the libc6 and libc6-686 packages... and I can't fix them, utterly impossible(from my point of view..).

oy.

what do I do now?

thanks,
Josh:-D

---

### Post by az on 2006-06-02
Install the debian libc6 packages by hand, and nothing else.

You should be able to run UBuntu packages with a later (debian testing) version of libc6.  Just remove the debian repositories from your list update and dist-upgrade to Dapper.


Oh, and don't mix repositories!

---

