---
title: "Programming with Java without an iDE?"
date: 2005-07-14
forum: Programming Talk
---

### Post by erik-the-red on 2005-07-14
I know from a prior thread I made that in order to compile and then run a C program, you do gcc [filename].c. If compilation is successful, an "a.out" file with be created. Do "./.a.out" to run the program.

How do I run a program after compilation using "javac" without an IDE?

---

### Post by dave9191 on 2005-07-14
when you javac MyClass.java

it generates the class file MyClass.class

To run that you do 

java MyClass

Dave

---

### Post by thumper on 2005-07-14
If you want to do java programming without an IDE, learn [ant](http://ant.apache.org/).

Good docs on the website.

---

### Post by charlieg on 2005-07-15
Ant really isn't necessary unless you're doing non-trivial projects.

Be sure to learn how to use a powerful editor like vim or emacs (or one of the more contemporary options) so you can work quickly.

As a previous poster points out, 'javac' compiles and 'java' runs.

---

### Post by Edric Technology on 2011-01-13
Hello, guys! Could you tell me wether we lose something programming this way (without IDEs) or not? :confused:

In Python for instance, using an IDE just help with code highlighting and other features, but it actually don't have any influence in the quality of programs. Is it the same thing with Java?


I have never programmed in Java before, and I don't like the widespread use-an-IDE practice. Thanks for the help!

---

### Post by tapasapat on 2011-01-13
Uhhh, a five years old topic. But anyways.

IDEs are just another tool to make your life easier. You still have to write the code yourself, the tool can only help with suggesting corrections etc. (*NetBeans is pretty smart, though, and even spots unnecessary loops and such. This could, in some way, be considered as "influencing the quality of programs".)

---

### Post by overdrank on 2011-01-13
> **tapasapat said:**
> Uhhh, a five years old topic. 

Agreed. thread closed :)

---

