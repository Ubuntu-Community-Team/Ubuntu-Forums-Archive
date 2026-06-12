---
title: "[SOLVED] C++ #include causing compiler infinite loop"
date: 2007-07-31
forum: Programming Talk
---

### Post by bluedalmatian on 2007-07-31
I'm sure this is a simple one but I cant find the answer anywhere.

If I have two classes A &B and each has a reference to the other, I need to #include A.h in B and B.h in A, but doing so seems to cause the compiler to go into an infinite loop.

Can someone please enlighten me as to the solution?

Thanks

---

### Post by the_unforgiven on 2007-07-31
> **bluedalmatian said:**
> I'm sure this is a simple one but I cant find the answer anywhere.

If I have two classes A &B and each has a reference to the other, I need to #include A.h in B and B.h in A, but doing so seems to cause the compiler to go into an infinite loop.

Can someone please enlighten me as to the solution?

Thanks
That's why you use the [guard-macros]("http://en.wikipedia.org/wiki/Include_guard").
This is not specific to C++, it's applicable to C as well (afterall, both are based on the same preprocessor).

---

### Post by hod139 on 2007-07-31
You need to use forward declarations to avoid the circular dependency.  
[http://www.parashift.com/c++-faq-lite/misc-technical-issues.html#faq-39.11](http://www.parashift.com/c++-faq-lite/misc-technical-issues.html#faq-39.11)
[http://en.wikipedia.org/wiki/Circular_dependency](http://en.wikipedia.org/wiki/Circular_dependency)

---

### Post by bluedalmatian on 2007-08-02
Thanks

---

### Post by rbprogrammer on 2007-08-02
i was just checking this thread out, but then i came across [http://en.wikipedia.org/wiki/Pragma_once](http://en.wikipedia.org/wiki/Pragma_once) and seeing that its non-standard but widely used, would it be "ok" or maybe beneficial to do something like:
```

#pragma once

#ifndef H_GRANDFATHER
#define H_GRANDFATHER

struct foo 
{
    int member;
};

#endif

```

i mean personally i always use the inclusion guards, but would this way have any pros than just doing the inclusion guards??

---

### Post by the_unforgiven on 2007-08-03
> **rbprogrammer said:**
> i was just checking this thread out, but then i came across [http://en.wikipedia.org/wiki/Pragma_once](http://en.wikipedia.org/wiki/Pragma_once) and seeing that its non-standard but widely used, would it be "ok" or maybe beneficial to do something like:
```

#pragma once

#ifndef H_GRANDFATHER
#define H_GRANDFATHER

struct foo 
{
    int member;
};

#endif

```

i mean personally i always use the inclusion guards, but would this way have any pros than just doing the inclusion guards??
You don't **need** pragma-once here - you already have the include guards.
And yes, #pragma once IS non-standard (in fact, any #pragma directive is non-portable - even among versions of the same compiler).
And, using #pragma once here won't have any pros.

---

### Post by hod139 on 2007-08-03
Include guards (and #pragma once directive) serve a different purpose, and do not prevent circular dependencies.  Include guards prevent a header from being included multiple times and defining the same thing multiple times.  Circular dependence is when class A depends on class B, and class B depends on class A.

As stated, the #pragma once directive is not standards compliant.  It was created many years ago by GCC, dropped to better adhere to standards compliance, then picked up again recently since so many other compilers support it.  The #pragma once directive replaces the include guard, so in your sample code you don't need the 
#ifndef
#define
...
#endif

 
I have been using the #pragma once more and more now.  As long as you are using gcc > 3.4 you are fine.  I personally like it better and find it cleaner than the include guards.  But, remember, it is not 100% portable.

---

### Post by noof on 2007-08-03
#pragma once was once faster than ordinary include guards since it just could skip the whole file when reaching the #pragma once. When using include guards its harder to do that, but this is almost not noticeable on newer versions of GCC. At work we use ordinary include guards in all files, and that's on a multi platform (pc/ps3/360), next-gen game which is my definition of a big project where small things matter :)

---

