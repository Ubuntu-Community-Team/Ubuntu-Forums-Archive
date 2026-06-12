---
title: "language to develop engineering app"
date: 2009-10-23
forum: Programming Talk
---

### Post by hambone79 on 2009-10-23
I am an engineer that is interested in creating a program to help engineers perform routine calculations (heat transfer, fluid mechanics, machine design, statics, etc.). I want to write something that is cross platform and has a simple GUI where the engineer can pick a topic from a drop down menu, then pick the calculator they are interested in running. Right now I have absolutely no idea what programming language I should use for this project, but here is a list of the requirements I need:

1. Something that is fairly easy to learn, or has enough in common with Perl that I can pick it up easy.
2. Something that will be easy to create a GUI in.
3. Something with built in math functions and the ability to handle vector/matrix math.
4. Something that is cross platform. At the very least it should run on Windows, Solaris, and Linux.

---

### Post by diesch on 2009-10-23
Have a look at [http://www.scipy.org/](http://www.scipy.org/)

---

### Post by hambone79 on 2009-10-23
That looks promising, but I need to add one more thing to my list of requirements:

5. The program needs to be easy to install so it should really be something that can be compiled to a binary. Basically I don't want to require the engineers downloading this program to install a Perl or Python interpreter.

---

### Post by diesch on 2009-10-23
Maybe that can be done using [http://pypi.python.org/pypi/bbfreeze/](http://pypi.python.org/pypi/bbfreeze/) (but I never tried).

---

### Post by shadylookin on 2009-10-23
I always thought enineers were supposed to love fortran:P

You could use c/c++

---

### Post by hambone79 on 2009-10-23
A friend of mine has volunteered to help me out so it looks like it will be written in Java.

---

### Post by Can+~ on 2009-10-23
> **hambone79 said:**
> A friend of mine has volunteered to help me out so it looks like it will be written in Java.

What a way to kill the fun :(.

But at least is portable (although people needs the JVM), and easy to make interfaces (Netbeans).

---

### Post by blwizard on 2009-10-24
> **hambone79 said:**
> A friend of mine has volunteered to help me out so it looks like it will be written in Java.

Java is a very solid choice, I would also possibly choose python.

---

### Post by mmix on 2009-10-24
LabWindows/CVI

[http://www.ni.com/lwcvi/](http://www.ni.com/lwcvi/)

---

