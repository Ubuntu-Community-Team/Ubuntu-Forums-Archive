---
title: "Objective-C"
date: 2008-08-07
forum: Programming Talk
---

### Post by Vegabondsx on 2008-08-07
Hello,

I am thinking about learning Objective-C since I use Macs a lot. I am also starting to become more and more of a Linux user as well. Objective-C is mostly used to program for OS X, but does anyone know if I can compile Objective-C programs for Linux as well?

Thanks

---

### Post by nvteighen on 2008-08-07
gcc can compile Objective-C. Just save your source code with .m as extension and type:
```

gcc -o test test.m -lobjc

```

But, I don't know if a program compiled in your Linux box will run in OS X. (you can download gcc into your Mac, of course).

---

### Post by nrs on 2008-08-07
Sure. Obviously you're SOL as far as Apple libraries are concerned, but the language itself is supported just as well as any other language GCC supports.

Maybe look into GNUStep.

---

