---
title: "[C preproc.] use #defined string for #ifdef"
date: 2008-07-08
forum: Programming Talk
---

### Post by flostre on 2008-07-08
Hi,

I'm in a group of around a dozen developers working on a software system which runs on a number of Linux distros in different versions. Among the libraries we use is GSL, which introduced a function I would like to use in its version 1.10. In older version I need a work-around. Normally, in such a situation I would use an #ifdef like this:

```
#ifdef GSL_1_10
// nice function
#else
// work-around
#endif
```

However, GSL does not define GSL_1_10, instead it does this:
```
#define GSL_VERSION "1.10"
```
Is there anyway of achieving the above effect using this constant? (Maybe in this special situation one could make use of the fact that "1.10" has four characters while older versions have only three.)

flostre

---

### Post by |{urse on 2008-07-08
should be just fine preceded by an #ifndef

---

### Post by flostre on 2008-07-08
I'm not sure I understand what you are sayin, |{urse. All versions of GSL #define GSL_VERSION, they just define it to different values. An "#ifndef GSL_VERSION" would not behave differently for different values of GSL_VERSION.

---

### Post by gnusci on 2008-07-08
I am afraid that is not possible, read **10.12** from:

[http://c-faq.com](http://c-faq.com)

But you can always ask for the **GSL** version with:

**gsl-config --version**

so just create the appropriate macro during your configure so you can use with the preprocessor latter.

---

### Post by flostre on 2008-07-08
thanks

---

### Post by balamadras on 2009-10-19
U can try as u do in scripting

#define GSL_VERSION "1.1.0"


#if $GSL_VERSION == 1.1.0
  // ur intended code
#else
  // other version code
#endif


All the Best !

---

