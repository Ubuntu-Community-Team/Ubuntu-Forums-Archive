---
title: "Using GCC on Uunbtu?"
date: 2009-03-09
forum: Programming Talk
---

### Post by efexD on 2009-03-09
I'm new to linux programming and I'm attempting to do C++ here. Is there any websites or can someone write me a brief tutorial how to compile and link a file on linux? That would be great

(C++)

---

### Post by geraldm on 2009-03-09
Please read the sticky in this forum.

---

### Post by WW on 2009-03-09
In particular, the "sticky" [Programming Tools and References](http://ubuntuforums.org/showthread.php?t=1006662) has a link to the [FAQ: Compiling your first C or C++ programs](http://ubuntuforums.org/showthread.php?t=689635).

---

### Post by nvteighen on 2009-03-10
Text editor + compiler. That's all you need.

(Well, actually, "all you need is love... Love is all you need")

---

### Post by abhilashm86 on 2009-03-10
you need to use g++ compiler to execute c++ programs,
install it from terminal,
```

sudo apt-get install g++

```
gcc dosen't support c++ programs.

you can refer this book, i'm refering this only, detailed two volumes.
[http://www.planetpdf.com/developer/article.asp?ContentID=6634](http://www.planetpdf.com/developer/article.asp?ContentID=6634)

---

### Post by jespdj on 2009-03-10
Install the package **build-essential**, not just the package g++ as abhilashm86 suggests.
```
sudo apt-get install build-essential
```
And, as already mentioned, read the stickies which explain everything in detail.

---

### Post by stevescripts on 2009-03-10
One more voice for reading the stickies ... ;)

Make sure you have installed build-essential.

You may find this thread useful: [http://ubuntuforums.org/showthread.php?t=981193](http://ubuntuforums.org/showthread.php?t=981193)

(see post #7 in that thread, for how to build a c++ program using gcc - 
then, dont do that.  Use g++ :) )

Good luck, and hope this helps a bit.

Steve

---

