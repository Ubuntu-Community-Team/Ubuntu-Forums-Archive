---
title: "Viking, GTK+ 2.2 and confusion....."
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Chilli Bob on 2008-08-13
OK, I'm trying to compile the new Viking GPS software.  I've found my missing dependencies, but now ./configure tells me this.....
```

checking for GTK+ - version >= 2.2.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: needs GTK+ 2.2.0

```Now, I don't know how to tell what version of GTK+ I have, but a quick visit to their website tells me the latest unstable version is 2.13.6, well short of 2.2.0.

Perplexed, I thought I'd install the GTK+ dev libraries through Synaptic and see if that helps in any way.  This may well be dumb reasoning, but I learn by trying stuff, so off I went.  But when I tried to mark a couple of suitable looking libs for installation I got errors that they could not be marked for installation because they (the libraries) had unresolved dependencies. i.e. 

 ```
libgtk2.0-dev:
         Depends: libgtk2.0.0 (=2.12.9-3ubuntu4) but
      2.12.9-4ubuntu3 is to be installed
```
and
```

    libgtk2.0-0-dpg:
       Depends: libgtk2.0-0 (=2.12.9-3ubuntu4) but
    2.12.9-4ubuntu3 is to be installed
```

Can anyone advise me......

1. How to see what version of GTK I have.  (I'm on Hardy will all updates)
2. Is there a GTK+ 2.2?
3. If so, how can I install it?

Thanks in advance for any help.

---

### Post by Chilli Bob on 2008-08-13
Bump!!

---

### Post by Vadi on 2008-08-13
Did you add any third-party repositories? On a clean Ubuntu install, libgtk2.0-dev installs fine. So it's only if you've added some other repositories that offer gtk (and not all of it) that this could happen.

---

