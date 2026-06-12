---
title: "C++ Repositioning the cursor"
date: 2006-08-27
forum: Programming Talk
---

### Post by enigma_0Z on 2006-08-27
Is there a quick (read: easy) way to move the cursor around on the screen in C++?

---

### Post by Woei on 2006-08-28
> **enigma_0Z said:**
> Is there a quick (read: easy) way to move the cursor around on the screen in C++?

You'll want to read up on ncurses, the standard terminal abstraction library for Unix. The ncurses library is in plain C though, but I'm sure you'll find a wrapper project or two to generate more idiomatic C++ code when googling around a bit.

---

