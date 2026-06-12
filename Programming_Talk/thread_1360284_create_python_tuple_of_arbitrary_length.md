---
title: "create python tuple of arbitrary length"
date: 2009-12-20
forum: Programming Talk
---

### Post by nbo10 on 2009-12-20
I want to create a tuple with an arbitrary length. I have the following code.

im = np.hstack((width,width))

I want to change the number of widths in the call to hstack. I might have (width,width,....width) with 100 widths. Is there a clever python trick I can use? Thanks

---

### Post by CptPicard on 2009-12-20
```

>>> width = 4
>>> (width,) * 5
(4, 4, 4, 4, 4)

```

---

### Post by nbo10 on 2009-12-20
Thanks, worked like a charm.

---

