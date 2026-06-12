---
title: "Explain shadow array?"
date: 2007-11-27
forum: Programming Talk
---

### Post by alexebird on 2007-11-27
Mr professor explained it a while ago, but I was trying to remember whats different about shadow arrays and I cant remember.  Anyone know?

---

### Post by iharrold on 2007-11-27
Never heard the term before.  What language?

---

### Post by alexebird on 2007-11-27
its not language specific actually, its a way of expanding the underlying array in a data structure thats implemented using fixed-sized arrays.  the main advantage if i can remember is that its a lot more efficient than expanding the array by copying every element in to a new, larger array.

---

### Post by dwhitney67 on 2007-11-28
Sounds similar to the concept of resize() in C++ STL vectors, or realloc() when dealing with C-style arrays.  I'm sure Java, perhaps Python have something similar.  Nevertheless, the term "shadow" is not widely used; perhaps just academia lingo.

---

