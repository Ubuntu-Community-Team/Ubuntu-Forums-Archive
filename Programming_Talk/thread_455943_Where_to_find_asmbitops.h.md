---
title: "Where to find asm/bitops.h"
date: 2007-05-27
forum: Programming Talk
---

### Post by dgovaert on 2007-05-27
I'm trying to compile an application on Ubuntu which I developed on a Debian box. I used the header file <asm/bitops.h> in my application but it seems to be unavailable on Ubuntu. How can I fix this?

Compiling works just fine since I was able to compile other apps.

Thanks
Dieter

---

### Post by moma on 2007-05-27
Not a very good answer, maybe not the correct one, but 

Read the [COLOR="Red"]**note 1)**[/COLOR] of this posting
[http://ubuntuforums.org/showthread.php?p=2728794#post2728794](http://ubuntuforums.org/showthread.php?p=2728794#post2728794)

$ dpkg -S bitops.h
will propably say the same.

---

### Post by dgovaert on 2007-05-27
Thanks for the tip I will try this out.

But I would like to find a more general solution so other could use my application w/o going through these troubles.

---

