---
title: "¿How to select a line in GtkTextView?"
date: 2017-06-10
forum: Programming Talk
---

### Post by enmanuelrz on 2017-06-10
Hello, i have a GtkTextView with a GtkTextBuffer named "buffer", and i trying to select the first line, i try with :
```

            TextIter siter;
            TextIter eiter;
            buffer.get_start_iter(out siter); //buffer is a GtkTextBuffer
            buffer.get_iter_at_line(out eiter,0);

```
but doesn't working.

How could I do it?

Thanks.

---

