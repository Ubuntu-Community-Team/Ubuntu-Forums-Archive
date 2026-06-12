---
title: "forcing ./configure into x86"
date: 2011-04-18
forum: Packaging and Compiling Programs
---

### Post by bluIT on 2011-04-18
Trying to install a module into lampp. I have successfully ran the phpize, ./configure, make, make install. But when i launch lampp (dev) i get,

```
Warning: PHP Startup: Unable to load dynamic library '/opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/ktaglib.so' - /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/ktaglib.so: wrong ELF class: ELFCLASS64 in Unknown on line 0
```

I am assuming this is because i run 9.10 (karmic) x64 and lampp is running as a x86 package (i think!). 
Is there a way to add a x86 argument to ./configure and force to build for x86 architecture?

---

### Post by bluIT on 2011-04-19
Managed to solve it :)
```

CPPFLAGS="-m32" ./configure 
```

---

