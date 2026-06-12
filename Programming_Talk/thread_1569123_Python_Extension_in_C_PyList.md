---
title: "Python Extension in C: PyList"
date: 2010-09-06
forum: Programming Talk
---

### Post by noobermin on 2010-09-06
Hye guys, I know I might not have made the best impression on this board, but this is a simple question for those who are more experienced with extending python: Does PyList's type's tp_dealloc call the tp_dealloc on each of its members? I can do the work of cleaning up myself, but I just don't want to reinvent the wheel.  Thanks

---

### Post by nvteighen on 2010-09-06
> **noobermin said:**
> Hye guys, I know I might not have made the best impression on this board, but this is a simple question for those who are more experienced with extending python: Does PyList's type's tp_dealloc call the tp_dealloc on each of its members? I can do the work of cleaning up myself, but I just don't want to reinvent the wheel.  Thanks

It should, I guess, only if the contained objects' references count down to zero... The docs seems to agree with me. But what are you doing?

---

