---
title: "G++ - option to don't register system/compiler data in binary."
date: 2009-10-08
forum: Packaging and Compiling Programs
---

### Post by Repgahroll on 2009-10-08
Hello there.

I'm compiling a simple command-line program, and i don't want to register the compiler version and other unused data in the binary.

I just know i did it before, but i forgot the compiler params/options :D.

You know... if you open (not run) the binary it's possible to find a bunch of lines like "GCC: (Ubuntu 4.3.3-5ubuntu4) 4.3.3", and some other references...

BTW... i tried to pack it using upx but it returns me an error (NotCompressibleException).

Thanks in advance.

PS: If someone also knows how to do this using the Netbeans IDE please lemme know!

---

### Post by snova on 2009-10-08
The **strip** utility can remove them, or you can use the **-fno-ident** option, however the latter method will still include the strings from other libraries.

```
strip -R .comment <program>
```

[http://www.trilithium.com/johan/2004/12/gcc-ident-strings/](http://www.trilithium.com/johan/2004/12/gcc-ident-strings/)

---

### Post by Repgahroll on 2009-10-09
Thank you very much!

---

