---
title: "Python embedding and extending"
date: 2009-04-15
forum: Programming Talk
---

### Post by zarqoon on 2009-04-15
I am trying to embed python in a software i am developing and i got the following problem.
I am using different local context dictionaries to run Python Code from different parts of my program. I have a c function exposed to python that is supposed to call a member function of a existing c++ object. 
The Problem is, that the there are more than one of these objects more precisely i have one of those for every local context i use.
I wrote a class that manages the local contexts in relation to the c++ objects and i can call python code using the appropriate local dictionary without problems. 
I need a way for my c function to know which Object to call the method on. It would be sufficient to get the PyObject* for the local dictionary i used to call the python code but i could not find out how to mangage that.

---

