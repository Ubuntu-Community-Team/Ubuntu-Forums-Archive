---
title: "Question about C++ templates"
date: 2009-02-23
forum: Programming Talk
---

### Post by krazyd on 2009-02-23
I have an implementation of the 'find' C++ standard library function:
```
// first implementation
template <class In, class X>
In find ( In begin, In end, const X& x ) {
  while (begin != end && *begin != x)
    ++begin;
  return begin;
}
```This seems to be correct and runs as expected. My question is, why does the following implementation not work?
```
// second implementation
template <class In>
In find ( In begin, In end, In* x ) {
  while (begin != end && *begin != x)
    ++begin;
  return begin;
}
```
It would seem to me that the second implementation is more correct, because it ensures that the type being searched for is the same as the type being referenced by the 'begin' and 'end' iterators. However it doesn't even compile. Is it possible to dereference a template type like that?

Also, in the first implementation, what is the significance of declaring 'x' as 'const X&' rather than just 'X'?

---

### Post by dwhitney67 on 2009-02-23
In the second example (the one that does not compile), the 3rd arg is a pointer to an iterator, not the value type that you presumably would want.  Don't confuse a pointer to an iterator with the de-reference of an iterator, which returns the value pointed to by the iterator.

The "const X& x" is used for two reasons... one is to ensure that you do not modify the value (access is read-only), and two, so that you do not create a copy of 'x' when the function is called; this helps with runtime performance.

P.S.  If you wanted to, the 3rd arg could be passed as a pointer, but then you would have to dereference the value when performing the comparison in your while-loop conditional.  The first example you have looks cleaner, although personally I would have chosen a different names than "In" and "X".  Perhaps "Iter" and "ValType" would be better?

---

### Post by krazyd on 2009-02-23
Thanks very much. I had forgotten the overloading of * in C++ means that, as you say, the third argument is a pointer to an iterator.

Things are much clearer now, cheers!

---

