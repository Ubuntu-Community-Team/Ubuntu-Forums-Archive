---
title: "Combining C++ and Python"
date: 2012-04-28
forum: Programming Talk
---

### Post by vanangamudi on 2012-04-28
I have written a todo task manager in C++. I want to save the tasks into an xml file. So i need a XML library. I tried libxml++. let us keep it aside. I want to use python for doing this job. can I combine python with C++. is there anyway to combine two languages in single program..

---

### Post by codemaniac on 2012-04-29
Have not tried it , but boost could be of help .
[http://www.boost.org/doc/libs/1_36_0/libs/python/doc/index.html](http://www.boost.org/doc/libs/1_36_0/libs/python/doc/index.html)

---

### Post by LemursDontExist on 2012-04-29
> **vanangamudi said:**
> can I combine python with C++. is there anyway to combine two languages in single program..

Yup.

Python is written in C, and you can [embed Python code]("http://docs.python.org/extending/embedding.html") in C or C++ using the Python C API.  You can also [extend Python]("http://docs.python.org/extending/extending.html") with a C or C++ module.

The documentation on this topic is quite extensive, so have a look!

EDIT: All that said, embedding isn't a great option because converting data from Python types to C types is very fiddly, so if your xml isn't very simple, it could be a good bit of work.  Extending Python is an option, but it's a poor fit if you've already implemented everything in C++.  Personally, I'd have done the whole project in Python, but at this point I would use a C++ based XML library.

---

### Post by jakovo on 2012-04-29
[LEFT]I dont know much about python but i know c++. Only thing i can recomend you is that you google  Cython which  is a programing langauge  to simplify writing c__ and  c++ extension modules.[/LEFT]

---

