---
title: "what to include with the exe?"
date: 2008-09-05
forum: Programming Talk
---

### Post by StOoZ on 2008-09-05
I've successfully installed C::B with wxwdigets on a windows machine.
now , I used monolithic=1 unicode=1 build=release and shared=1 for the wxwidgets build.
the app works when I start it from C::B , but I would like to distribute it , the exe + the required files (DLLs?) , what files do I need to pack up with the exe??

I've tried asking it over the C::B forums , and I got topic locked :mad:
[http://forums.codeblocks.org/index.php/topic,9129.0.html]("http://forums.codeblocks.org/index.php/topic,9129.0.html")

---

### Post by rnodal on 2008-09-05
You got it. The executable plus any DLL it depends on.

-r

---

