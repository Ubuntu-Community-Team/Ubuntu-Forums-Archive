---
title: "what is -fPIC gcc compile option"
date: 2007-12-17
forum: Programming Talk
---

### Post by monkeyking on 2007-12-17
Hi,
I'm doing some cross language programming (calling C from R).
And I get the following error.

```

/usr/bin/ld: myProg.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC

```
I don't really understand the error, and I've never heard about -fPIC.

thanks in advance

---

### Post by geraldm on 2007-12-17
In much older versions of the compiler gcc there was a flag "-fPIC" which was an abbreviation for Position Independent Code, and this had to be passed to create library code objects, without that flag, code that is specific to the source would be used, and then the library would fail.

Gerald

---

### Post by wolfbone on 2007-12-17
[http://people.redhat.com/drepper/dsohowto.pdf](http://people.redhat.com/drepper/dsohowto.pdf)

The "-fPIC" flag is still in gcc 4.2.2 (fortunately!)

---

### Post by the_unforgiven on 2007-12-18
> **wolfbone said:**
> [http://people.redhat.com/drepper/dsohowto.pdf](http://people.redhat.com/drepper/dsohowto.pdf)

The "-fPIC" flag is still in gcc 4.2.2 (fortunately!)
An absolute must-read for anyone dealing with shared objects (shared libraries) with any bit of seriousness :)

---

