---
title: "preprocessor conditionals on g++ version"
date: 2008-11-23
forum: Programming Talk
---

### Post by monkeyking on 2008-11-23
Is it possible to do preprocessor conditionals on the version of gcc. like
```

#if GCC_version< 4.0
#define old_defines
#endif

```


Futhermore is it possible to have diffent #defines for differnet platforms,

thanks if advance

---

### Post by snova on 2008-11-23
Yes. The macro is __GNUC__. I think there's another one.

There are also predefined macros for differing architecures, but I don't know what they are except 'i386'.

---

### Post by PaulFr on 2008-11-23
Perhaps **_[http://gcc.gnu.org/onlinedocs/gcc-4.1.2/cpp/Common-Predefined-Macros.html](http://gcc.gnu.org/onlinedocs/gcc-4.1.2/cpp/Common-Predefined-Macros.html)_** will help.

---

### Post by monkeyking on 2008-11-24
I solved this,
for anyone reading this, a complete list of defines can be given with
[PHP]
echo "main(){}" | g++ -E -x c++ -dM - 
[/PHP]

The solution is this
[PHP]
#define GCC_VERSION (__GNUC__ * 10000 \
                               + __GNUC_MINOR__ * 100 \
                               + __GNUC_PATCHLEVEL__)

/* Test for GCC > 3.2.0 */
#if GCC_VERSION > 30200
[/PHP]
But I can only make the compareson work for the ">" not "==" or "<".

This must be an error of mine?

---

