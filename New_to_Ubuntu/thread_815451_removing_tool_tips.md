---
title: "removing tool tips"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by fminmexico on 2008-06-01
How do you stop tool tips they are the most annoying thing about Ubuntu you cannot see anything because of them.
   fminmexico.

---

### Post by ibuclaw on 2008-06-01
Press "**Alt+F2**" to open the Run Application bar, type in **gconf-editor** and run.

Then go into "**apps>panel>global**" in the gnome registry and uncheck the value of the key **tooltips_enabled** at the bottom of the list.

I think that is what you're looking for (Hover your mouse over an icon the tooltips for it won't appear).

Regards
Iain

---

