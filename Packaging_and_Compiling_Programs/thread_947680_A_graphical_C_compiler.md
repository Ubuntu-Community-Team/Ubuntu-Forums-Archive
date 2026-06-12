---
title: "A graphical C compiler?"
date: 2008-10-14
forum: Packaging and Compiling Programs
---

### Post by Jshaw on 2008-10-14
My teacher is planning on using Redhat for teaching us linux this year, but she said that she might consider ubuntu if there was a C compiler. Is there a graphical c compiler available for ubuntu?

---

### Post by Shin_Gouki2501 on 2008-10-14
"graphical complier" krkr thats funny ^^
(yes call this unimportant, but still i found it funny :)

---

### Post by LaRoza on 2008-10-14
> **Jshaw said:**
> My teacher is planning on using Redhat for teaching us linux this year, but she said that she might consider ubuntu if there was a C compiler. Is there a graphical c compiler available for ubuntu?

Exactly how would this work?

If you mean an IDE, then there is.

Don't confuse IDE's with compilers. 

The C compiler in most common use is GCC. 

For Ubuntu:

```

sudo aptitude install build-essential

```

To get an IDE, there are many, but for an class you described, I'd recommend Geany:

```

sudo aptitude install geany

```

See the stickies on tools for finding more IDE's.

---

### Post by Jshaw on 2008-10-16
forgive me for not knowing the big boy words Shin.

---

### Post by Ecclesiastes on 2008-11-15
There's not a "graphical" compiler, but considering the breadth of options and depth of directives that can be submitted to gcc, it would make sense to write a GUI script of check boxes and field fills to build the gcc command line: a graphical make.

It would even be a good project for your class.

---

### Post by Kazade on 2008-11-18
[Code::Blocks]("http://www.codeblocks.org/") is a pretty good MSVC-like IDE if you need something a bit more feature-ful than Geany (which is really nice but really lightweight)

---

### Post by bubba_169 on 2008-11-18
> **Kazade said:**
> [Code::Blocks]("http://www.codeblocks.org/") is a pretty good MSVC-like IDE if you need something a bit more feature-ful than Geany (which is really nice but really lightweight)

I'd go for Code::Blocks too. Its a great IDE for anyone switching from MSVC and I use it myself for any projects. It simplifies all of the compiling, linking, etc into one simple button :D

---

### Post by Tomato-kun on 2008-11-20
i prefer Eclipse... it also can be used for other languages.

---

### Post by Kazade on 2008-11-20
I like Eclipse for Java, and it manages OK with PyDev for Python. However, I don't think it copes well with C/C++, especially if you have "Build Automatically" turned on, compiling C/C++ takes too long for this to work properly in my experience. I also think the moment you start installing more than 2 or 3 plugins into Eclipse it turns into a massive resource hog.

I haven't tried CDT in a while though, it might have improved. I use Eclipse daily for Java and Python, but switch to Code::Blocks for C++ when I'm at home.

---

### Post by skirkpatrick on 2008-11-20
I use Eclipse at work for C/C++.

---

### Post by meatpan on 2008-11-20
I recommend using 'ddd'.  It isn't a graphical compiler (or a compiler at all), but it does allow you to isolate and walk through the components of the compilation process (such as linking and pre-compiling).  I found ddd to be very helpful when I started learning about the principals of compilation and executable formats.

---

### Post by cmat on 2008-11-20
There is a GUI application called Kompile which helps compile source tarballs. I think it's in the repos.

---

