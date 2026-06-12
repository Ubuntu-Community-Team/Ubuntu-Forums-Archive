---
title: "Simple Cairo question"
date: 2009-05-23
forum: Programming Talk
---

### Post by cl333r on 2009-05-23
I'm painting a blue rectangle then a white one atop of it.
Yet I can see the blue rectangle, any idea why it happens or how to fix it?

```

Cairo::RefPtr<Cairo::Context> cr = ...
cr->set_source_rgb(0,0,1);//blue
cr->rectangle(x, y, width, height);
cr->stroke();

cr->set_source_rgb(1, 1, 1);//white
cr->stroke();

```

PS: never mind the purpose of this, I need it for a reason

---

### Post by Victor Liu on 2009-05-31
Your first stroke command should be a stroke_preserve; in its present form the second stroke has no path to operate on. I'm writing this from memory, so this may not be the problem, but I think it is.

---

