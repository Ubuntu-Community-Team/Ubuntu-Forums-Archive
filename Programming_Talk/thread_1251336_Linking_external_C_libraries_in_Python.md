---
title: "Linking external C libraries in Python"
date: 2009-08-27
forum: Programming Talk
---

### Post by jounihat on 2009-08-27
I'm embedding some C code to my Python program, but I'm having problem linking external libraries (math and allegro) to the compiler. This is how the C program works with GCC:

```
gcc -lm render.c -o render.o `allegro-config --libs`
```

How can I transform this to the Python's setup.py file so that it will link the necessary libraries as needed?

---

