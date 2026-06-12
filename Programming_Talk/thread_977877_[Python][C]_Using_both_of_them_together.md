---
title: "[Python][C] Using both of them together?"
date: 2008-11-10
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-10
Hello...
I consistently hear that one of the better ways of programming resource not-hungry programs is by embedding C within Python....which sounds pretty cool, to be honest. However, for all the references, I can't seem to find the *how* of it.

So,
A) I'd consider myself a Python "mid-beginner" (as nvteighen puts it)--or: ) pretty good grasp of if/while/for/else/simple data structures, moderate grasp of OOP. And a C "Well, I know the syntax...." Is this actually a good idea, or should I wait a while?
B) If so, how?

Thanks.

<off-topic style="arrogance">Yay! 300þ post!</off-topic>

---

### Post by LaRoza on 2008-11-10
> **fiddler616 said:**
> Hello...
I consistently hear that one of the better ways of programming resource not-hungry programs is by embedding C within Python....which sounds pretty cool, to be honest. However, for all the references, I can't seem to find the *how* of it.

There are several ways, what is the goal of using C with Python here?

> 
<off-topic style="arrogance">Yay! 300þ post!</off-topic>

That is about three days work.

---

### Post by fiddler616 on 2008-11-10
> **LaRoza said:**
> There are several ways, what is the goal of using C with Python here?

Well, I mean it generally, but I foresee the most common usage being writing math-heavy loops in C, and UI/data structures in Python (you gotta love dictionaries).
> 

That is about three days work.I apologize for my mortal standards, O Mighty One.

---

### Post by LaRoza on 2008-11-10
> **fiddler616 said:**
> Well, I mean it generally, but I foresee the most common usage being writing math-heavy loops in C, and UI/data structures in Python (you gotta love dictionaries).

There are several ways of using C with Python. You can write C modules, embed C directly into Python, or use tcc in Python (and probably others).

[http://www.python.org/doc/2.5.2/api/api.html](http://www.python.org/doc/2.5.2/api/api.html)

> 
I apologize for my mortal standards, O mighty one.
Capital "M" and "O", please.

---

### Post by fiddler616 on 2008-11-11
> **LaRoza said:**
> There are several ways of using C with Python. You can write C modules, embed C directly into Python, or use tcc in Python (and probably others).

[http://www.python.org/doc/2.5.2/api/api.html](http://www.python.org/doc/2.5.2/api/api.html)
Sweet, looks like I have some reading to do!
[quote=The Mighty One]
Capital "M" and "O", please.[/quote]
Fixed. Excuse me while I go atone. :)

---

### Post by Paul Miller on 2008-11-11
> **fiddler616 said:**
> Well, I mean it generally, but I foresee the most common usage being writing math-heavy loops in C, and UI/data structures in Python (you gotta love dictionaries).


One thing to keep in mind is that there are pre-made C extensions for many of these sorts of things.  For example, in your use case, you should consider python-scientific (scipy).  Also, python-psyco (psyco) can frequently give a significant boost to this type of code, without needing to resort to a C extension, by adding 2 lines to your source file.

---

### Post by crazyfuturamanoob on 2008-11-12
If you wish to have python in C, then you should do this:
```

#include <Python.h>

```
And you need to have python-dev installed.
Also, when compiling, you need to have these options when compiling:
> 
-I/usr/include/python2.5/ -lpython2.5


To use it:
```

/* start python interpreter */
Py_Initialize();

/* run a string in python interpreter */
PyRun_SimpleString("a = 5");

/* shut python interpreter down */
Py_Finalize();

```

---

### Post by fiddler616 on 2008-11-12
> **crazyfuturamanoob said:**
> 
```


/* run a string in python interpreter */
PyRun_SimpleString("a = 5");


```
Thanks! But...is it really that cumbersome? Or could I go crazy and do:
```
PyRun_SimpleString("
a = 5
spam = 'eggs' #Dang, no double quotes allowed
dict = {"crazyfuturamanoob" : "Ubuntu Forums" , "La Roza" : "Ubuntu Forums ex-mod"}
print 'Hello World!'
#Finish this madness:
"
//There goes the Python
printf("Goodbye, World!")

```
?

Thanks, all of you (definitely going to look into SciPy and Pysco too)

---

### Post by fiddler616 on 2008-11-12
<completely off-topic>
You may notice that LaRoza has burnt beans.
She has been banned.
Read: [http://laroza77.blogspot.com/2008/11/ubuntuforumsorg-banning.html](http://laroza77.blogspot.com/2008/11/ubuntuforumsorg-banning.html)
This is a shame for us, the Programming Talk community.

Why am I posting this?
A) I don't know how many of you read her blog, and therefore know the 'real scoop'
B) I don't want to make this a separate thread, 
> 
[B]Originally posted by LaRoza's blog:
[/B]Please do not PM the admins, make threads, or make any fuss over the issue. It is only my right to contest it, and I'm not going to.
So don't make a fuss either, just a quiet second of silence of lamentation over the loss of a valued member.
In a word:
Darnit!
</completely off-topic>

---

### Post by snova on 2008-11-12
I get the forboding feeling of Thread Closed...

Python can be used with C, but if you are not yet very experienced with C, I would suggest you stay away from this for now. C is complicated enough by itself, but now you're trying to mix it with something completely different.

But when you get to it, there is very good documentation (as is the case with all of Python) in the Python reference. If you have not done so already, you should install it locally from the python2.5-doc package.

---

### Post by fiddler616 on 2008-11-13
> **snova said:**
> 
Python can be used with C, but if you are not yet very experienced with C, I would suggest you stay away from this for now. C is complicated enough by itself, but now you're trying to mix it with something completely different.

Now that I think about it a bit more, that's probably a good idea, I'll hold off for a while (for instance, when I count my lines of code in thousands, not dozens).....
[/THREAD (unless somebody has something especially insightful to say)]

---

