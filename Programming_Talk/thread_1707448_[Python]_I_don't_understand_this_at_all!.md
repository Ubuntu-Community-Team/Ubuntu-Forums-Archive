---
title: "[Python] I don't understand this at all!"
date: 2011-03-15
forum: Programming Talk
---

### Post by raf-kig on 2011-03-15
Obviously I'm a Python noob...
```
>>> L = [[0,0]]*10
>>> L
[[0, 0], [0, 0], [0, 0], [0, 0], [0, 0], [0, 0], [0, 0], [0, 0], [0, 0], [0, 0]]
>>> L[5][1] = 7
>>> L
[[0, 7], [0, 7], [0, 7], [0, 7], [0, 7], [0, 7], [0, 7], [0, 7], [0, 7], [0, 7]]

```How can I modify only the element located at L[5][1] ?

---

### Post by robots.jpg on 2011-03-15
The way you're creating  the list in the first place is giving you 10 references to the same [0,0]  list object.  Try this instead:
 ```

 L = [[0,0] for i in range(10)]
 
```

---

