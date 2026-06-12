---
title: "Mixing C++ and Python for Simulations"
date: 2013-02-16
forum: Programming Talk
---

### Post by Dirich on 2013-02-16
Hello,

I write programs in C++ using the eigen and mpfr libraries to run simulations of physical systems. Which means my programs do mathematical computations with arbitrary precision arithmetic.

What I am thinking is to use Python to handle everything that is not the computations: Data Input and Output (which is simply writing files), etc.

I have tried to read a bit around, but due to my inexperience with Python (I never used it up to now), I would like to have some expert opinion on the topic. Am I going to have problems? If so, which ones? Etc. etc.

My doubts are born from these points:

[LIST=1]
[*]I sometime use arbitrary precision type from the library mpfr. I know python has no problem with this type of numbers, but passing them to a C function and receiving them as a return value from them... can these be problematic?
[*]I always use matrices. Specifically, I use the eigen Matrix types (dynamic dimension), if I want to use Python to handle all the file I/O I need to pass these specific types as return value (actually a pointer to one, or an array, of them)
[*]If I do all the I/O in Python, I am going to have Python calling C++ calling Python. I suppose this shouldn't be too much of a problem, but still... is it going to be so? I only mixed C, C++ and Fortran up to now, and no one of them is an interpreted language
[/LIST]


Is there anyone that already tried to do something like this? Do you have any suggestion? I.e. use cpickle for handling the data I/O, etc.


Thank you!

---

### Post by SuperCamel on 2013-02-16
Have you read [this?]("http://docs.python.org/2/extending/extending.html") I think creating a python extension module is the only real option here. I believe you will find answers to all of your doubts after you've created a simple extension module or two. 

The problem is, python modules are generally written in C. Writing them in C++ is possible, but it's not as easy. Check out PyCXX on sourceforge. 

[I found this tutorial helpful.]("http://www.tutorialspoint.com/python/python_further_extensions.htm")
[]("http://www.tutorialspoint.com/python/python_further_extensions.htm")

---

