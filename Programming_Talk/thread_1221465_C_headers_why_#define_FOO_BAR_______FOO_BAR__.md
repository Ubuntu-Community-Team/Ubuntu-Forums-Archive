---
title: "C headers: why #define FOO_BAR     __FOO_BAR__?"
date: 2009-07-23
forum: Programming Talk
---

### Post by marlinman on 2009-07-23
I'm trying to determine the value of the constant FLT_EPSILON on my system but in float.h all I see is 

"#define FLT_EPSILON     __FLT_EPSILON__"

In fact every constant in this header seems to be defined along similar lines! Where then can I find the value of __FLT_EPSILON__ and what exactly is the point of #defines like the one quoted above (as opposed to say "#define FLT_EPSILON 0.00000000132432")?

---

### Post by soltanis on 2009-07-23
It's been defined in terms of some other internal constant (I really don't know why but GCC really likes to do this). Look at what headers the header includes, and check through them for the __FLT_EPSILON constant.

By the way, __FOO_BAR is generally used for "internal" (hidden to the programmer) constants in the gcc convention. If you search through header files, you see that you run into this kind of thing often.

---

### Post by marlinman on 2009-07-23
Thanks Soltanis - it did occur to me to check for any includes in float.h but there are none! So I'm stumped!

I did try a grep in /usr/lib and found that __FLT_EPSILON__ is defined in /usr/lib/perl/5.10/Config_heavy.pl to be ~1.19e-7F but doubt this is relevant(?).

---

### Post by soltanis on 2009-07-23
Then maybe the preprocessor knows this definition itself. It's possible that when it sees __FLT_EPSILON__ it automatically replaces the value with some pre-defined constant.

If you really need to know what it is I suggest you do

```

#include <float.h>

int main() {
         printf("%f", FLT_EPSILON);
         return 0;
}

```

Compile & run.

---

### Post by marlinman on 2009-07-23
Aww now I feel stupid soltanis :-)

Thanks for that - I needed to add a precision modifier tho' (to see anything but 0.000000)!

---

