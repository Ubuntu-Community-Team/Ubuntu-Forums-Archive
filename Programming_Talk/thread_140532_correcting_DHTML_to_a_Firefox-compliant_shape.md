---
title: "correcting DHTML to a Firefox-compliant shape"
date: 2006-03-06
forum: Programming Talk
---

### Post by Van_Gogh on 2006-03-06
Hi,

I'm a avid user of a database with economic data regarding [the Faroe Islands]("http://en.wikipedia.org/wiki/Faroe_islands")(lovely place!) and also I use Mozilla Firefox. An example of the database frontend can be seen [here]("http://www.hagstova.fo/portal/page?_pageid=33,126415&_dad=portal&_schema=PORTAL"). Now, because the database frontend has been designed for Internet Explorer, I got an annoying problem.

Because some of the data descriptors(inside the table) are wider than the current width, in IE you can pull those black vertical arrows to increase/decrease its width. This is however not possible in Mozilla Firefox. Anyone know if it would be difficult to get those vertical arrows to work in Mozilla Firefox?

---

### Post by stoffe on 2006-03-06
At a quick glance it seems like it would be quite easy to correct, but I may have missed something. First off, the site uses IE only window.event to get the events, a simple solution for this can be seen here: [http://www.quirksmode.org/js/events_access.html#link5](http://www.quirksmode.org/js/events_access.html#link5)

After correcting that, some of the element accessing code may or may not need to be changed into getElementById() style code, which works in all modern browsers including IE - it may just work as it is too, I don't really remember how good the support is in non-IE for 20th century javascript. ;)

---

