---
title: "Frame size * larger than 1024"
date: 2011-11-16
forum: Packaging and Compiling Programs
---

### Post by ufuser01 on 2011-11-16
Hi,

Whenever I am compiling certain programs, I am getting this (gcc 4.4.x). This is not an issue on gcc 4.3. On gcc 4.4, I could use -Wframe-larger-than=2048 to suppress this. 

1. What does this warning signify? 

2. What happens if the frame is larger than 1024? 

3. What is a frame in this context?

Thanks.

---

### Post by Bachstelze on 2011-11-16
```
       -Wframe-larger-than=len
           Warn if the size of a function frame is larger than len bytes.  The computation done to determine the
           stack frame size is approximate and not conservative.  The actual requirements may be somewhat greater
           than len even if you do not get a warning.  In addition, any space allocated via "alloca", variable-length
           arrays, or related constructs is not included by the compiler when determining whether or not to issue a
           warning.

```

[http://en.wikipedia.org/wiki/Call_stack](http://en.wikipedia.org/wiki/Call_stack)

You are probably allocating too many things on the stack. Post your code.

---

