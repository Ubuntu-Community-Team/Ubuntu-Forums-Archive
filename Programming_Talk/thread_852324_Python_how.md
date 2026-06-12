---
title: "Python how?"
date: 2008-07-07
forum: Programming Talk
---

### Post by diwas on 2008-07-07
Hello there, 
Im not new to the programming world but completly newbie to Python, which i wanted to learn so badly. Now here's the chance, i guess.
I would like to request to you guys to tel me how should i proceed. This includes which package i have to install, and appropriate IDE for it. I dont know anything about Python so if there is a good e-book link you have, i would like to know about it. 
Thank you.

---

### Post by LaRoza on 2008-07-07
> **diwas said:**
> Hello there, 
Im not new to the programming world but completly newbie to Python, which i wanted to learn so badly. Now here's the chance, i guess.
I would like to request to you guys to tel me how should i proceed. This includes which package i have to install, and appropriate IDE for it. I dont know anything about Python so if there is a good e-book link you have, i would like to know about it. 
Thank you.

On Ubuntu: Use Gedit ("Text Editor") and Python is already installed. Check out the sticky for learning it (or my site and wiki)

On Windows: See my wiki or pmasiars wiki.

You don't need an IDE, but IDLE comes with the ActivePython installer, and Gedit with its plugins is more than enough.

---

### Post by master_kernel on 2008-07-07
**Tutorials:**
[http://www.diveintopython.org/](http://www.diveintopython.org/)
[http://docs.python.org/tut/](http://docs.python.org/tut/)

**IDE:** [http://pythonide.blogspot.com/](http://pythonide.blogspot.com/)

```
sudo apt-get install python2.5
```

---

### Post by pmasiar on 2008-07-07
LaRoza means wiki in my sig: collected best links from internet, for Python beginners, including training tasks. Enjoy!

---

### Post by LaRoza on 2008-07-07
> **pmasiar said:**
> LaRoza means wiki in my sig: collected best links from internet, for Python beginners, including training tasks. Enjoy!

I thought it was your wiki? 

My wiki links to it pretty quickly anyway. It is also in the sticky.

(Now we know why it is called a "web" :-))

---

### Post by diwas on 2008-07-07
> **LaRoza said:**
> I thought it was your wiki? 

My wiki links to it pretty quickly anyway. It is also in the sticky.

(Now we know why it is called a "web" :-))

Hehehe

Thanks a lot for the reply.
I have 98% migrated to ubuntu, therefore this new (for me) and powerfull(i have heard from many) is to be learnt in this os!!

Im starting rightaway!!

Thank you again.

---

### Post by Kiefer Rodriguez on 2008-07-07
I learned Python from the free eBook 'Dive Into Python' by Swaroop C. H., I suggest you check that one out, Python should be installed by default on your system.
A few links,

[http://www.awaretek.com/tutorials.html]("http://www.awaretek.com/tutorials.html#test") - Over 300 free Python Tutorials/eBooks/HOWTO's
[Projects for the Beginner]("http://www.daniweb.com/forums/thread32007.html") - A forum thread from DaniWeb full of idea's for the beginner to undertake.

If you find yourself stumped on a problem, consider hopping on IRC onto #python (on irc.freenode.com).

I wish you the best of luck, Python is a great language.
~Kiefer

---

### Post by sp0nge on 2008-07-07
As far as an IDE goes, I've always been partial to IDLE.

---

### Post by pmasiar on 2008-07-07
As I mention in my wiki :-) if you have some programming experience, "Dive into Python" is good. If not, see wiki for other :-)

Project Euler has great training tasks, after doing simple ones you may want to look at Python Challenge website, with puzzles specially for Python: solving puzzle "unlocks" next level. With forums for each level.

---

### Post by diwas on 2008-07-08
How do i compile by using gedit?? I have the codes but dunno how to compile it.

---

### Post by nanotube on 2008-07-08
> **diwas said:**
> How do i compile by using gedit?? I have the codes but dunno how to compile it.

python is an interpreted language, don't need to compile anything. you can just run your code using the python interpreter. (e.g., if your python source file is "mycode.py", you can run from terminal using command "python mycode.py")

---

### Post by Greyed on 2008-07-08
There is no compiling in Python.

Wellllll, there is, but not in the traditional sense.  You just run the scripts directly.  It should be covered in any tutorials that have been mentioned above.

---

### Post by diwas on 2008-07-08
Oh, Im sorry i ddnt know that. I will try it.
Thank you.

Edit: Its done!!

---

### Post by -grubby on 2008-07-08
> **Greyed said:**
> 
Wellllll, there is, but not in the traditional sense.  You just run the scripts directly.  It should be covered in any tutorials that have been mentioned above.

It compiles to Byte code

---

### Post by pmasiar on 2008-07-08
> **Greyed said:**
> There is no compiling in Python.

Wellllll, there is, but not in the traditional sense.  You just run the scripts directly.  It should be covered in any tutorials that have been mentioned above.

When you run "python mycode.py", python compiler looks for presence of mycode.pyc, and for it's timestamp. If .pyc file is more recent, it will be used (also if .py is not found).

.pyc file is parsed and compiled to bytecode, ready to be run by Python virtual machine (but compared to Java VM, code is compiled to binary only by special request). New PyPy will be able to compile to statically typed code (by requests) based on type info gathered at runtime, which will eliminate the 20% performance penalty of dynamic typing.

---

### Post by diwas on 2008-07-08
"Python is the most poerfull and effective programming language till now." Is this true? coz i have heard this from a professional programmer.

---

### Post by pmasiar on 2008-07-08
> **diwas said:**
> "Python is the most poerfull and effective programming language till now."

Yes, for some (average) values of "powerful and effective". For most people, yes: depends on what you program of course.

---

### Post by nanotube on 2008-07-08
> **diwas said:**
> "Python is the most poerfull and effective programming language till now." Is this true? coz i have heard this from a professional programmer.

depends on the task at hand. :) please see the sticky about programming language "wars", it's all been said and re-said before. :)

---

### Post by diwas on 2008-07-08
Great. 
I dont know where amI heading wid Python. I have no vision what will I be doing with it in future. 
...Damn im confused.

---

### Post by ghostdog74 on 2008-07-08
> **diwas said:**
> Great. 
I dont know where amI heading wid Python. I have no vision what will I be doing with it in future. 
...Damn im confused.

learn how to make lotsa money instead, by not programming.

---

### Post by diwas on 2008-07-08
And how can this be done??? Money..hehe sounds good!!

---

