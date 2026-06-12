---
title: "[R, G, B, R, G, B ...] -&gt; [B, G, R, B, G, R ...]: most effcient way in C?"
date: 2010-08-20
forum: Programming Talk
---

### Post by Senesence on 2010-08-20
More specifically: 

[PHP]
void rgb_to_bgr(char* image, size_bytes){
    // image = [R, G, B, R, G, B ...]
    // use the most efficient method to change it into:
    // [B, G, R, B, G, R ...]
}
[/PHP]

---

### Post by dwhitney67 on 2010-08-20
Well, let's see... the 'G' character never changes position, so therefore it looks like you merely need to change the 'R's and the 'B's.

Maybe something like:
```

void rgb_to_bgr(char* image, unsigned int size_bytes)
{
   for (register unsigned int i = 0; i < size_bytes; i += 3)
   {
      image[i]     = 'B';
      image[i + 2] = 'R';
   }
}

```

P.S.  If the string actually has different values that are not specifically 'R', 'G', and 'B', then use temporary variable to hold the value.
```

void rgb_to_bgr(char* image, unsigned int size_bytes)
{
   char tmp;

   for (register unsigned int i = 0; i < size_bytes; i += 3)
   {
      tmp          = image[i];
      image[i]     = image[i + 2];
      image[i + 2] = tmp;
   }
}

```

---

### Post by saulgoode on 2010-08-20
Using pointers would eliminate some of the array indexing, though most modern compilers would equivalently optimize dwhitney's source resulting in machine code that is just as fast.

```

void rgb_to_bgr(char* image, unsigned int size_bytes) {
  register char tmp;
  char *endp = &image[size_bytes];

  for (char *p=image; p < endp; p += 3) {
    tmp = *p;
    *p = p[2];
    p[2] = tmp;
    }
 }
```

---

### Post by Senesence on 2010-08-21
Yea, iterating over the array, in segments of 3, and changing R to B and B to R was my initial approach.

I was just thinking: "Maybe there is some neat pointer/bit shift mojo to doing it really, really quickly".

I guess the obvious approach is the most efficient in this case.

Thanks guys.

---

### Post by jpkotta on 2010-08-21
> **Senesence said:**
> Yea, iterating over the array, in segments of 3, and changing R to B and B to R was my initial approach.

I was just thinking: "Maybe there is some neat pointer/bit shift mojo to doing it really, really quickly".

I guess the obvious approach is the most efficient in this case.

Thanks guys.

The slowest thing is probably the memory access, not the actual swap operation.  There are ways to optimize cache usage: [http://lwn.net/Articles/255364/](http://lwn.net/Articles/255364/).  But as always, profile to make sure optimization is even worthwhile.

---

### Post by Devport on 2010-08-21
> **Senesence said:**
> I was just thinking: "Maybe there is some neat pointer/bit shift mojo to doing it really, really quickly".

I guess the obvious approach is the most efficient in this case.
There is a bit magic way of swapping values ( avoiding the use of a temporary variable ), but with modern compilers its probably best to let them decide ( based on arch / compile options ) :

[http://en.wikipedia.org/wiki/Xor_swap_algorithm](http://en.wikipedia.org/wiki/Xor_swap_algorithm)

---

### Post by saulgoode on 2010-08-21
> **Senesence said:**
> I was just thinking: "Maybe there is some neat pointer/bit shift mojo to doing it really, really quickly".

I guess the obvious approach is the most efficient in this case.
Efficiency is somewhat relative. Code can be "efficient" with regard to execution speed, code size, memory usage, platform portability, and/or maintainability. That the solution be provided in C places a high priority on the last two criteria, yet this limits the available options for increasing efficiency with regard to speed, size, or memory.

Also, keep in mind that the suggested "brute force" approach is not as inefficient (with regard to speed) as it might seem at first blush. While the code suggests that the data is fetched from memory a byte at a time, and temporarily stored and retrieve from a memory variable (tmp), most compilers would catch that a processor register can be used for the 'tmp' variable; and on many microprocessors the memory data will be cached on-chip in relatively large blocks that are read from or written to RAM using fast paging (where entire "rows" of memory will be accessed in bursts). In addition, processor pipelining would permit some of the data accesses and arithmetic to be performed simultaneously.

As a final comment, if you were to consider coding in processor-specific assembly language then you might be able to optimize things better with regard to speed, but to do so you would most likely need to do some degree of [loop unwinding]("http://en.wikipedia.org/wiki/Loop_unwinding"). This will necessitate some pre-conditions on your image dimensions; for example, that the number of pixels must be a multiple of 12.

---

