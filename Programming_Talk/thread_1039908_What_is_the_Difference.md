---
title: "What is the Difference"
date: 2009-01-15
forum: Programming Talk
---

### Post by peter.devon on 2009-01-15
hi all,

 What is the Difference between realloc() and free()? Please reply soon.

Thanks
-----------------------------
[http://www.infysolutions.com]("http://www.infysolutions.com")

---

### Post by jpkotta on 2009-01-15
```
sudo aptitude install manpages-dev
man realloc # they're on the same manpage
```

realloc() doesn't free memory (well, it could, but after it returns there is still allocated memory).  It's functionally the same as free()ing and then malloc()ing again.

---

### Post by eye208 on 2009-01-15
> **jpkotta said:**
> It's functionally the same as free()ing and then malloc()ing again.
No, it's not.

realloc() will resize an allocated block without losing its content. This is very different from free() + malloc(). Once you call free(), the content is gone.

---

### Post by jpkotta on 2009-01-15
> **eye208 said:**
> No, it's not.

realloc() will resize an allocated block without losing its content. This is very different from free() + malloc(). Once you call free(), the content is gone.

Very true.  I need to stop posting so late at night.

---

### Post by snova on 2009-01-15
Their entire purpose. ;)

malloc() allocates memory.
calloc() allocates memory and initializes it to zero.
free() releases memory.
realloc() changes the size of an allocated memory block.

---

### Post by CptPicard on 2009-01-16
> **snova said:**
> 
realloc() changes the size of an allocated memory block.

With the gotcha that the pointer that comes back from realloc may or may not be the same pointer that went in. Content is not lost, but there can be copying going on in the background.

---

