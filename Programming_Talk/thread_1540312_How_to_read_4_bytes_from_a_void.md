---
title: "How to read 4 bytes from a void *"
date: 2010-07-27
forum: Programming Talk
---

### Post by genux05 on 2010-07-27
Hi all,

I was wondering how do read a byte, or even a 4 byte field from a void *.

fread would read from a file, but the void * has already been read in, it is part of a project that I am working on but the data appears to not be correct (about twice as much in a integer value than what I was thinking was the correct value).

---

### Post by Bachstelze on 2010-07-27
What do you mean by "read"? If you want to copy n bytes from one area of memory to another, you can use memcpy().

---

### Post by WitchCraft on 2010-07-27
Like this:

[http://aimbots.net/tutorials/19870-how-read-instruction-cache.html](http://aimbots.net/tutorials/19870-how-read-instruction-cache.html)
(my tutorial)

---

### Post by genux05 on 2010-07-27
Thanks for the responses, I was having a brain dead day today and completely forgot about memcpy 

Thanks again

---

