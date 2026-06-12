---
title: "specialized templates in cpp"
date: 2008-03-24
forum: Programming Talk
---

### Post by StOoZ on 2008-03-24
im reading a book (C++), and I still cant understand what is so special about specialization in templates, I would be very happy if someone can explain it in short... :(

10x

---

### Post by heikaman on 2008-03-24
in short, templates are generic which means they can handle different types with the same code, but sometimes you want to treat a certain type in a special way, that's what specialization is.
it's like saying “this function will handle all types except  integers (specialization)  I want to handle them with another function”.
that's all :)

---

