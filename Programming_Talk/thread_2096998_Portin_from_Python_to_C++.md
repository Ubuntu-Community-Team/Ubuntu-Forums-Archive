---
title: "Portin from Python to C++"
date: 2012-12-21
forum: Programming Talk
---

### Post by lykwydchykyn on 2012-12-21
So, I'm mostly a Python guy, and I have some open source projects in Python/QT.  I'd like these to run better on older systems, and I'm contemplating porting some of them to C++.

I'm not really a C++ guy, though; I've taken classes on it, read books on it, and seen enough of it (hard to avoid if you work with QT), but I've never really developed anything in it.

I'm not looking for a C++ tutorial; I know the basics.  I guess what I'm looking for is some help or advice on how to approach C++ when coming from a higher-level language.  

Anyone have any thoughts on this?

---

### Post by na5h on 2012-12-21
Perhaps this will help:
[http://web.cse.msu.edu/~cse231/python2Cpp.html](http://web.cse.msu.edu/~cse231/python2Cpp.html)

---

### Post by DTSDeveloper on 2012-12-21
Actually a better transition would be:
python -> php -> c++
the transition should be easy: i did it the opposite way
i know this would hijack your post, but i have quick question for you. i know this seems "noobish" but i have never had this problem in any other language. when im printing literal strings and then variables, it prints the variable with a space on either side. so if the value is "cat" it becomes " cat ".
if i do strip(" ") will that work? is there a better function?

---

### Post by Vaphell on 2012-12-21
you mean python's *print a, b, c* that will print "value_of_a value_of_b value_of_c"?

it works that way. If you want string as a single blob with no separation you need to use formatting string, similar in its concept to printf() function

```
>>> a=333
>>> b="xyz"
>>> print "----%d----%s" % (a,b) # printf style formatting string
----333----xyz
print "----{1}----{0}".format(a,b) # newer python formatting
----xyz----333
```
[http://www.python.org/dev/peps/pep-3101/](http://www.python.org/dev/peps/pep-3101/)

in newer versions of print (in v2.6 you have to use *from __future__ import print_function* statement) - it allows to define separator and line end

```
>>> print( a, b, sep="^", end="=\n" )
333^xyz=
```

---

### Post by DTSDeveloper on 2012-12-21
ok so c style then thank you

---

### Post by Vaphell on 2012-12-21
i'd say newer python style is much more powerful and it's not that different than C-style (% placeholders are replaced by {} placeholders, nothing spectacular), because it allows to define alignment, padding and whatnot right off the bat. Look at the examples
[http://docs.python.org/2/library/string.html](http://docs.python.org/2/library/string.html)
also parameters can be named so you don't have to maintain order.

---

### Post by DTSDeveloper on 2012-12-21
thanks that really helps

---

### Post by SuperCamel on 2012-12-21
> **lykwydchykyn said:**
> So, I'm mostly a Python guy, and I have some open source projects in Python/QT.  I'd like these to run better on older systems, and I'm contemplating porting some of them to C++.

I'm not really a C++ guy, though; I've taken classes on it, read books on it, and seen enough of it (hard to avoid if you work with QT), but I've never really developed anything in it.

I'm not looking for a C++ tutorial; I know the basics.  I guess what I'm looking for is some help or advice on how to approach C++ when coming from a higher-level language.  

Anyone have any thoughts on this?

I don't think it would be too difficult. I'd start by defining the classes and member functions first, and then define member variables as required. Remember you've got the option to make members private or protected now too! 

I'd image the biggest challenge would be when it comes to string manipulation. Nothing difficult though, if you've got a good C++ reference and an understanding of the python code.

---

### Post by lykwydchykyn on 2012-12-22
> **na5h said:**
> Perhaps this will help:
[http://web.cse.msu.edu/~cse231/python2Cpp.html](http://web.cse.msu.edu/~cse231/python2Cpp.html)
Thanks; that's a good start, but kind of basic.  
> **DTSDeveloper said:**
> Actually a better transition would be:
python -> php -> c++
the transition should be easy: i did it the opposite way


I do a lot of PHP coding as well.  I think the challenge is that most C++ materials teach you all the low-level, built-in stuff and ignore the STL or library features.  Do C++ programmers really work with arrays most of the time, or are there good abstractions out there for, say, collection classes (lists, dictionaries/hashes, tuples, etc)?

> **SuperCamel said:**
> I don't think it would be too difficult. I'd start by defining the classes and member functions first, and then define member variables as required. Remember you've got the option to make members private or protected now too! 

I'd image the biggest challenge would be when it comes to string manipulation. Nothing difficult though, if you've got a good C++ reference and an understanding of the python code.

Right now the biggest thing that sends me for a loop are pointers.  I understand what they are, I just don't always understand why they get used when they do.  I read C++ code (for example, the code snippets on this page: [http://doc.qt.digia.com/qt/webkit-fancybrowser.html](http://doc.qt.digia.com/qt/webkit-fancybrowser.html)) and it's completely non-obvious to me why sometimes variables are declared as pointers and sometimes not.

---

### Post by GeneralZod on 2012-12-22
> **lykwydchykyn said:**
> 
I do a lot of PHP coding as well.  I think the challenge is that most C++ materials teach you all the low-level, built-in stuff and ignore the STL or library features.  Do C++ programmers really work with arrays most of the time,

Gosh, no - using arrays directly is [strongly discouraged](http://www.parashift.com/c++-faq-lite/arrays-are-evil.html).


> or are there good abstractions out there for, say, collection classes (lists, dictionaries/hashes, tuples, etc)?



Yes to all - std::list, std::map, and (in C++11 onwards) std::unordered_map and std::tuple.  If you are using Qt, you can use the [Qt containers](http://doc.qt.digia.com/qt/containers.html) which have a (IMO) much nicer API than their often weirdly named and clunky STL counterparts, although they are not built for raw performance.  Since this is a port of a Python app, though, this probably won't make much difference.  Qt's QString class is also something I would much prefer to use over std::string.

> 
Right now the biggest thing that sends me for a loop are pointers.  I understand what they are, I just don't always understand why they get used when they do.  I read C++ code (for example, the code snippets on this page: [http://doc.qt.digia.com/qt/webkit-fancybrowser.html](http://doc.qt.digia.com/qt/webkit-fancybrowser.html)) and it's completely non-obvious to me why sometimes variables are declared as pointers and sometimes not.

Qt handles a lot of [memory management](http://blog.sobbayi.com/memory-management-guide-for-qt-c/) for you, so some things are always allocated on the heap as Qt will eventually delete them for you.  As a rule of thumb, objects that derive from QObject are almost always allocated on the heap.

Any specific questions that you run into, please ask away :)

---

### Post by SuperCamel on 2012-12-22
> **lykwydchykyn said:**
> 
Right now the biggest thing that sends me for a loop are pointers.  I understand what they are, I just don't always understand why they get used when they do.  I read C++ code (for example, the code snippets on this page: [http://doc.qt.digia.com/qt/webkit-fancybrowser.html](http://doc.qt.digia.com/qt/webkit-fancybrowser.html)) and it's completely non-obvious to me why sometimes variables are declared as pointers and sometimes not.

Yeah I dunno if I understand all the reasons for using pointers. One reason is because it's quicker and more efficient to create copies of a pointer than to create copies of an entire class. 

Rule of thumb though, don't use pointers unless you need to.

---

### Post by zombifier25 on 2012-12-22
I'm still a learner so I'm also interested in what pointers are primarily used for.

But I do know one use of pointers in C++ is taking advantage of inheritance and polymorphism. Those 2 features are useful in some cases (I took advantage of them in my Uno playing program by declaring the classes Human and AI as inheriting from Players, and have the Players morph into Human or AI)
Also, Qt programs and books usually encourage you to use pointers and "new" them instead of declaring the objects directly. Still dunno why

---

### Post by lykwydchykyn on 2013-01-04
I wanted to get back to this conversation with an example of what confuses me about pointer use.

See the code examples on this page:

[http://zetcode.com/gui/qt4/layoutmanagement/](http://zetcode.com/gui/qt4/layoutmanagement/)

Notice that in verticalbox.cpp all the widgets are created as pointers using "new".

But in main.cpp, "window" is just created directly.

Why is it different?

---

### Post by GeneralZod on 2013-01-04
> **lykwydchykyn said:**
> I wanted to get back to this conversation with an example of what confuses me about pointer use.

See the code examples on this page:

[http://zetcode.com/gui/qt4/layoutmanagement/](http://zetcode.com/gui/qt4/layoutmanagement/)

Notice that in verticalbox.cpp all the widgets are created as pointers using "new".

But in main.cpp, "window" is just created directly.

Why is it different?

window isn't given a parent, so Qt doesn't delete it for you - therefore, it's safe to handle destruction yourself.  May as well just allocate it on the stack :)

---

### Post by lykwydchykyn on 2013-01-04
> **GeneralZod said:**
> window isn't given a parent, so Qt doesn't delete it for you - therefore, it's safe to handle destruction yourself.  May as well just allocate it on the stack :)

Would it be safe to generalize that I should only create qobjects/qwidgets on the stack if:

 - They only need to exist temporarily during a function call (e.g. dialog box)
 - I'm in main(), and thus the program will be done when the function returns.

Fair enough?

---

### Post by GeneralZod on 2013-01-04
> **lykwydchykyn said:**
> Would it be safe to generalize that I should only create qobjects/qwidgets on the stack if:

 - They only need to exist temporarily during a function call (e.g. dialog box)
 - I'm in main(), and thus the program will be done when the function returns.

Fair enough?

Add "and they aren't given a parent", and that sounds like a good rule - I can't think of any exceptions offhand.

---

