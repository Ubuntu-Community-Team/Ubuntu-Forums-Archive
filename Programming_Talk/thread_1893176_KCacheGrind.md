---
title: "KCacheGrind"
date: 2011-12-09
forum: Programming Talk
---

### Post by karlson on 2011-12-09
Everyone I need to have dispute settled with regards to KCacheGrind.

When KCacheGrind reports the information per function it report basically 3 columns:

INCL   SELF   Called

The dispute here is the following:

INCL is:

[LIST=1]
[*]The Average of the sum of the time that the program spent inside the function itself and functions it calls
[*]The sum of total times that the function spends in itself and functions it calls. Expressed as total time
[*]The sum of total times that the function spends in itself and all the functions it calls expressed as a percentage of total program run time.
[/LIST]

I've already tried KCacheGrind documentation but it is causing a brain dump in me for the moment.

---

### Post by karlson on 2011-12-09
I think I found my answer:

[http://stackoverflow.com/questions/1093138/kcachegrind-interpretation-confusion](http://stackoverflow.com/questions/1093138/kcachegrind-interpretation-confusion)

---

