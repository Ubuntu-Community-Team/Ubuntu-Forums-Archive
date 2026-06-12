---
title: "How does a compiler solve nested inline functions? (c++)"
date: 2013-02-25
forum: Programming Talk
---

### Post by Dirich on 2013-02-25
I am wondering how a compiler would proceed in writing the following code:

```

inline void f1() {...}
inline void f2() {... f1() ...}

main()
{
      ...
      f2()
      ...
}

```

My doubt concerns the option the compiler has about inlining or not.
Is its concern only the length of the code after the inline takes place?

Also, let's assume that solving f1() first, inlining it into f2(), causes the compiler to choose not to inline f2() into main but to keep it as a normal function.
Is it possible that if the compiler had tried to inline f2() first, then f1() could be inlined too (thus obtaining a radically different code from the previous case)?
If so, is there a way for me to force one or the other behavior?

---

