---
title: "help making debs"
date: 2010-05-21
forum: Packaging and Compiling Programs
---

### Post by coolman98 on 2010-05-21
I was wondering how to make package my  programs I am very much a beginner and want to learn how to
make debs. if anyone thinks that would be too hard i would like to learn how to make tarballs.:)

---

### Post by lykwydchykyn on 2010-05-21
Making tarballs is trivial:
```

tar -czf myprogram.tar.gz directoryContainingMyProgram/

```

Making debs can be consirably more involved, depending on what kind of program it is and how portable you want the deb to be.

The [Ubuntu packaging guide](https://wiki.ubuntu.com/PackagingGuide) is a good place to start.

---

### Post by coolman98 on 2010-05-21
I would like to be able to ./configure, make and make install it any suggs?

---

### Post by lykwydchykyn on 2010-05-21
What language are your programs written in?  

I believe what you need to look into is GNU autoconf.

---

### Post by coolman98 on 2010-05-21
c++

---

### Post by lykwydchykyn on 2010-05-21
Maybe check this out:
[http://sources.redhat.com/autobook/autobook/autobook_toc.html](http://sources.redhat.com/autobook/autobook/autobook_toc.html)

---

### Post by coolman98 on 2010-05-21
thanks.

---

### Post by Sealbhach on 2010-05-21
Maybe you could try [checkinstall]("http://www.asic-linux.com.mx/%7Eizto/checkinstall/"), though I'm not sure if it will meet all your needs.

.

---

