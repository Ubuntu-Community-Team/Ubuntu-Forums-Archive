---
title: "Is it possible to make a 'widget' like program in Java"
date: 2007-03-10
forum: Programming Talk
---

### Post by speedsix on 2007-03-10
i.e one that is..

transparent and undecorated so unable to close with the x or minimise
always underneath everything else, i.e fixed to the desktop



Thanks

Dom

---

### Post by phossal on 2007-03-10
A JWindow, with no default close operation?

---

### Post by speedsix on 2007-03-12
How would I ensure it never had focus and remained underneath everything, i.e pinned to the desktop?


Thanks


Dom

---

### Post by Hendrixski on 2007-03-12
What about with the Google Web Toolkit.  That's Java based, and it does Widgets.  They're not just browser-based though, are they?

Also, if you google Java Widget then there are a lot of links that come up.  So... yes, it's possible, I've never tried it.  :)

---

### Post by phossal on 2007-03-12
What are you really trying to accomplish? A glasspane and custom event handlers can *deflect* focus. You don't even want to be able to *alt-tab* the window into focus?

---

