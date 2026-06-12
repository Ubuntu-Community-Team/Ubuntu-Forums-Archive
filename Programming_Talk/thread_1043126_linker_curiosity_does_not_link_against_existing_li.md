---
title: "linker curiosity: does not link against existing library"
date: 2009-01-18
forum: Programming Talk
---

### Post by Kraut~salat on 2009-01-18
hi, compiling a program via > g++ -o avcodec_sample avcodec_sample.cpp -lavformat -lavcodec I receive a couple pf linker errors, like this one: > avcodec_sample.cpp:(.text+0x3e7): undefined reference to `avcodec_alloc_frame()'

Funny, because I added the "-lavcodec" option to the g++ call. The library does exist, as
> tim@calculus:~/Code$ locate libavcodec.so
/usr/lib/libavcodec.so
shows.

and > tim@calculus:~/Code$ nm -D /usr/lib/libavcodec.so | grep avcodec_alloc_frame
000deae0 T avcodec_alloc_frame
tells me that the library contains the required symbol. So why can I not link the program?

Thx

---

### Post by Zugzwang on 2009-01-18
Just a guess: The function is declared in some .h header file, right? Probably the header file is not C++-compatible, i.e. it does not contain something like:

```

#ifdef __cplusplus
extern "C" {
#endif

....The content....

#ifdef __cplusplus
}
#endif

```

Try to include the header files for that library the following way:
```

extern "C" {
  #include <foobar.h>
}

```

The reason: C and C++ use different function decorations.

---

### Post by Kraut~salat on 2009-01-18
you are my savior, that was exactly the problem. But what I don't is why exactly? The program did compile without a problem, only the linking failed. So if it didn't include the headers correctly the problem should have already occured when compiling.

But thank you.

---

### Post by Zugzwang on 2009-01-18
> **Kraut~salat said:**
> you are my savior, that was exactly the problem. But what I don't is why exactly? The program did compile without a problem, only the linking failed. So if it didn't include the headers correctly the problem should have already occured when compiling.


No, because ... well ... see here: [http://en.wikipedia.org/wiki/Name_mangling](http://en.wikipedia.org/wiki/Name_mangling)

---

### Post by Kraut~salat on 2009-01-18
wow, one never stops learning.

I didn't know that C++ internally changes function names. C doesn't. No surprise the linker cannot find the (transformed) function names.

---

