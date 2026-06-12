---
title: "(C/C++)+Python"
date: 2010-09-12
forum: Programming Talk
---

### Post by weezerBo on 2010-09-12
Hello, 

I'm going to be writing some software (image processing/game), and the performance in Python just doesn't cut it in certain areas -- I base this on past experience and test implementations of my code. I've also gotten some Python wizards to try and optimize it and they can't come close.

I know 100% I'm going to have to use C/C++ in certain areas. However, Python in such a wonderful language to write in the thought of using C/C++ as sole the programming languages(s) makes me want to cry. 

So I'm wondering if anyone has any good resources on mixing the two. 

One particular question that I have on my mind is whether to write the core/kernel/host/entry-point/whatever-the-correct-term in C and layer Python on top of that somehow. Or if I should be using Python as the entry point and use C solely for expensive functions.

---

### Post by worksofcraft on 2010-09-12
Definitely your second approach will be best. Just use C/C++ for time critical functions and also I'm very interested in learning how to do this too... so I'll be lurking on your progress reports ;)

---

### Post by ghostdog74 on 2010-09-12
do your speed critical portion in C++ by extending Python.

---

### Post by DanielWaterworth on 2010-09-12
There are several approaches to mixing c/c++ and python, I prefer swig, but there are others like Boost for example.

---

### Post by James78 on 2010-09-12
Here's a few useful links.. [This]("http://docs.python.org/extending/extending.html"), [this]("http://www.boost.org/doc/libs/1_44_0/libs/python/doc/index.html"), and [that]("http://www.swig.org/Doc1.3/Python.html").

---

