---
title: "calloc or malloc ?"
date: 2011-07-16
forum: Programming Talk
---

### Post by lucasart on 2011-07-16
hello

i'm wondering whether to use malloc or calloc in C. calloc zero initializes the memory, but is there any other difference ?
i need to allocate a potentially large chunk of memory, and I do want to zero initialize it. So should I do malloc and memset, or just calloc ?

thanks

---

### Post by NovaAesa on 2011-07-16
I would just use calloc. As far as I know there is a no difference between malloc + memset to 0 and calloc.

---

### Post by johnl on 2011-07-16
If you want to zero-initialize the memory, use calloc.

If you don't care about the memory contents or you are planning to overwrite the memory immediately with some (mostly non-zero) data, use malloc.

---

### Post by Bachstelze on 2011-07-16
calloc will be faster on most OSes (I tested on Linux and OS X, I expect most POSIX OSes to be the same, no idea about Windows). Do you really need to zero-fill the memory, though?

---

### Post by nvteighen on 2011-07-16
My € 0.02:

By default, I use calloc() because it ensures me that the memory has been initialized to a value I know. Even if I'm going to overwrite it immediately after; it's safer and I'm absolutely not concerned about losing miliseconds of CPU time.

---

### Post by lucasart on 2011-07-16
> **Bachstelze said:**
> calloc will be faster on most OSes (I tested on Linux and OS X, I expect most POSIX OSes to be the same, no idea about Windows). Do you really need to zero-fill the memory, though?
Thanks. Yes, I do in the precise context where I use it need zero initialization. Although I really don't mind writing a memset call just after.
What I'm mostly worried about is memory limitations. Can I imagine calloc-ing something like 256 MB of RAM ? or is it better to use malloc for that.
as for the actuall speed of the function itself, it's not important here. only executed once during some program initialization function.

---

### Post by MadCow108 on 2011-07-16
calloc is probably to be faster than malloc +memset, but it should really not matter, just use the simpler calloc. Both functions should have the same limitations (= it might be hard to allocate a huge continuous block depending on memory fragmentation and kernel version).

I prefer malloc + MALLOC_PERTURB_ when I don't need initialized to zero memory, it sets the content of the memory buffer to some (preferably large) value
it helps finding bugs

calloc'd memory can hide bugs , e.g. when you unintentionally access it but the code will still work because its zero:
e.g. code like this:
```

memory_Value = &wrong_calloc_memory_location;
for(int i=0; i < *memory_value; i++) 
  // do something important but does not cause a crash when skipped
```
can often work due to *memory_value being zero, but when it was malloc'd with MALLOC_PERTURB_ it is likely that you will notice the bug earlier.

---

