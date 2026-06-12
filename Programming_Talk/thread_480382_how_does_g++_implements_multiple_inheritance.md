---
title: "how does g++ implements multiple inheritance?"
date: 2007-06-21
forum: Programming Talk
---

### Post by angustia on 2007-06-21
hi

somebody knows how, at low pointer, level, does g++ implements multiple inheritance? 

how it does to make inherited methods to access the correct fields of an instance of a class even if it's not a direct child...?

i know that an inherited method can correctly access fields in a derived class because the inherited fields are stored first in the instance, and new fields are added at the end, so the first part of the instance is a exact image of an instance of the parent class. But this is not always true with multiple inheritance.

i have two ideas about how it can be done:

- making an adapter class on demand (this is simpler, and slower)
- storing more than one VMT in the instance, and using stub code that corrects the "this" pointer (this is more complex to explain).

but those are just ideas and i wish to know how realy this thing is done

thanks in advance
excuse my english

---

