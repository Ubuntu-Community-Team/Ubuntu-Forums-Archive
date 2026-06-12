---
title: "Compiling only a part of kdebase (or any other large project)"
date: 2007-04-03
forum: Programming Talk
---

### Post by MadMonkey234 on 2007-04-03
Hi,

I downloaded the source of kdebase using apt-get source kdebase and then I proceeded to some customizations in kicker. Then I made a package with dpkg-buildpackage -rsudo and it works just fine. Now let's say I forgot something and I want to change something else in kicker, is there a way I can avoid to rebuild the whole kdebase (which takes about an hour) and only rebuild kicker and install it after? I mean I can rebuild the whole thing but it's a waste of time....

Thanks

---

### Post by GeneralZod on 2007-04-04
Once you've compiled the whole thing, you can usually just navigate to kdebase/whereever and do make && sudo make install.  Note that this will circumvent the package manager, but for small changes this generally makes no difference.

---

