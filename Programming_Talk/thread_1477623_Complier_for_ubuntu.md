---
title: "Complier for ubuntu??"
date: 2010-05-08
forum: Programming Talk
---

### Post by ferjonathas on 2010-05-08
Im trying to write the C code cuz its sample.. I basically learning.. Im stuck at the compling part.  Do I need a program if so each one??

---

### Post by Sealbhach on 2010-05-08
It's the GNU compiler, the package is called gcc.

Here's a very simple example of how to compile a hello world:

[http://www.network-theory.co.uk/docs/gccintro/gccintro_9.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_9.html)

.

---

### Post by unmole on 2010-05-08
If you are learning C, I suggest you install geany. It is an integrated development environment which simplifies and speeds up the whole process.

---

### Post by lisati on 2010-05-08
Moved to "Programming talk"
Have a look here: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by phrostbyte on 2010-05-09
[gcc]("apt:build-essential") & [geany]("apt:geany")

(Click links for repository auto downloads)

---

### Post by Tony Flury on 2010-05-09
> **unmole said:**
> If you are learning C, I suggest you install geany. It is an integrated development environment which simplifies and speeds up the whole process.

For a beginner, using an IDE is bad advice in my opinion. A begiiner should be learning about the compiler, linker and probably Makefiles - so that they can understand some of the error conditions and likely challenges.
I would use an IDE once a user is comfortable creating and building 3 or 4 file projects by hand.

Also - you will actually not just need gcc (which I think is installed by default) - you will also need the "build-essential" package which contains loads of the libraries etc.

```

sudo apt-get install build-essential

```

Best advice in my opinion is to read the sticky posts in this forum about your favourite language.

---

