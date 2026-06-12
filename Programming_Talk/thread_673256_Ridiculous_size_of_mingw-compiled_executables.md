---
title: "Ridiculous size of mingw-compiled executables"
date: 2008-01-20
forum: Programming Talk
---

### Post by breaking on 2008-01-20
When I compile my program with g++ it comes out around 100KB.. just the generic
```
g++ file1.cxx file2.cxx file3.cxx file4.cxx
```

When I compile the same program with 
```
i586-mingw32msvc-g++ file1.cxx file2.cxx file3.cxx file4.cxx
```

The executable is almost **_3 megabytes_**!

The exe is going right to my prof's Windows machine (we have to turn in a binary with our projects) so are there any flags that I can give the compiler to reduce filesize, like using Windows libraries that will be present on his machine?

---

### Post by breaking on 2008-01-20
Anyone?

---

### Post by Acglaphotis on 2008-01-20
[http://www.mingw.org/mingwfaq.shtml#faq-cpp-size](http://www.mingw.org/mingwfaq.shtml#faq-cpp-size)

---

### Post by breaking on 2008-01-20
WOW that was just the trick! 3MB to 100kb. Thanks

---

### Post by Acglaphotis on 2008-01-20
No problem, anytime!

---

