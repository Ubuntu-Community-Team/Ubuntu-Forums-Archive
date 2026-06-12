---
title: "touch screen"
date: 2010-01-09
forum: Programming Talk
---

### Post by plusnplus on 2010-01-09
Hi..,
Which programming language is more suit to develop touch screen application?
The application is for food/ drink ordering (with drag and drop).

Thanks for any info

---

### Post by skullmunky on 2010-01-09
Do you need multitouch or just regular touch?

if multitouch it gets a little trickier, but generally it's not a matter of the language but of the gui toolkit you choose.  Also it depends on whether it's for waitstaff and just has to work really well, or for customers and has to look pretty and have shiny animations and things.

for functionality i'd look at GTK, Wx, and Qt, not necessarily in that order and build it in python.

you could also look at Pygame, and if you need a lot of animated glitz, you might try Flex.

---

### Post by plusnplus on 2010-01-09
Hi skullmunky,
Thanks for the info.
I do not need animation in the program. as long as the drag and drop function working that's fine.
Btw, do you know where i can find sample/ demo drag and drop that link to database.
I tried search by google, but so far only find drag and drop without link to database.

---

