---
title: "Dbus &amp; Strigi"
date: 2008-08-05
forum: Programming Talk
---

### Post by gorilla on 2008-08-05
As Kde4 does not seem to have a useful search client for Strigi/ Nepomuk, I thougt about fiddling something together in python.
However, I cannot suss out how to get search hits from dbus.

I explored the methods with qdbusviewer, but the promising sounding ones don't work.
For example, in vandenover.strigi/search/vandenover/strigi I can use *countHits*; It returnes the number of hits for the given keyword.
But when I call the method *getHits* the answer is "Unable to find method getHits" although it is listed by dbus.

So.. how do I make Strigi dance via dbus?

---

