---
title: "Python and API help"
date: 2010-05-09
forum: Programming Talk
---

### Post by Lex-Man on 2010-05-09
Two quick questions,

Is there a list of the API's that are standard in Ubuntu.  I'm guessing GTK2.

Is there a list of docs like the Java docs for Ubuntu.

Second if Python does not require compiling it does that mean it uses JIT compiling and how does that effect preference of Python programs.

---

### Post by Tony Flury on 2010-05-09
> **Lex-Man said:**
> Two quick questions,

Is there a list of the API's that are standard in Ubuntu.  I'm guessing GTK2.

The best list of API's is here : [http://docs.python.org/index.html](http://docs.python.org/index.html). GTK is available - in the form of pyGTK : [http://library.gnome.org/devel/pygtk/stable/index.html](http://library.gnome.org/devel/pygtk/stable/index.html) - but there are other GUI toolkits available that work on Gnome - for instance Tkinter, Qt etc - and also there is KDE and others.

> **Lex-Man said:**
> 
Is there a list of docs like the Java docs for Ubuntu.

Not that I know of - but there are loads of tutorials etc on line.

> **Lex-Man said:**
> 
Second if Python does not require compiling it does that mean it uses JIT compiling and how does that effect preference of Python programs.
Python is compiled - ".py" files are compiled into ".pyc" when there are first executed - and the interpreter looks for ".pyc" files first.

What did you mean about preferences - do you mean performance (i.e. speed) ? It is generally accepted that you should not use Python for maths intensive operations, but there are maths libraries available for Python which have been written in lower level languages. It reals does depend on what is important to you.

---

### Post by Lex-Man on 2010-05-09
> **Tony Flury said:**
> The best list of API's is here : [http://docs.python.org/index.html](http://docs.python.org/index.html). GTK is available - in the form of pyGTK : [http://library.gnome.org/devel/pygtk/stable/index.html](http://library.gnome.org/devel/pygtk/stable/index.html) - but there are other GUI toolkits available that work on Gnome - for instance Tkinter, Qt etc - and also there is KDE and others.


Not that I know of - but there are loads of tutorials etc on line.


Python is compiled - ".py" files are compiled into ".pyc" when there are first executed - and the interpreter looks for ".pyc" files first.

What did you mean about preferences - do you mean performance (i.e. speed) ? It is generally accepted that you should not use Python for maths intensive operations, but there are maths libraries available for Python which have been written in lower level languages. It reals does depend on what is important to you.

I kind of interested in writing some Linux programs.  I pretty much a java dev but I have some C++ experience as well.  I am looking at doing some stuff in C++ although I'm also interested in Python as I have read the XDCD comics.  I'm also looking at Mono development.  I just wanted to know about what libraries were available in Ubuntu I have installed Geany and wanted to try and make some basic programs to see what I want to focus on.

---

### Post by Tony Flury on 2010-05-09
There are loads of "standard" libraries available including ones to ftp, HTML, XML, RPC, email etc - have a look at the standard library section at docs.python.org.

There are also toolkits like pyGTk (to do GUIs), pyGame (a tool kite for games, including sprites collision etc). And loads of 3rd Party APIs to interface to loads of stuff.

---

### Post by Portmanteaufu on 2010-05-09
> **Tony Flury said:**
> 
Python is compiled - ".py" files are compiled into ".pyc" when there are first executed - and the interpreter looks for ".pyc" files first.


This is true, but might be a little misleading to a beginner. Python uses a "Virtual Machine" to run code. Essentially, when you write code in Python, it gets boiled down into Python bytecode before it gets run. Python bytecode is lower level than Python, but it isn't native code running on your computer. The bytecode still requires the Python interpreter to run. This is different from what one would typically think of when they hear "Compiled Language". For instance, when we talk about C++ being a compiled language, we mean that our C++ code gets turned into native machine code that runs entirely on its own.

As Tony Flury mentioned, once the interpreter has turned some code into bytecode it will save it off as a .pyc file so it doesn't have to convert it again the next time you run it. This saves plenty of execution time.

> **Tony Flury said:**
> 
It is generally accepted that you should not use Python for maths intensive operations, but there are maths libraries available for Python which have been written in lower level languages. It reals does depend on what is important to you.


To build on what Tony said, Python is written in C. The great part about this is that whenever you hit a piece of code that you feel is running too slowly, you can rewrite that same code in C (which is debatably the fastest language) and then use the new code from Python. In a lot of common cases (like intensive math libraries), someone else will have already done this for you. It's just a matter of searching for it.

For most purposes, though, Python is plenty fast. It's understandably easy to get caught thinking that "Python is slower than C, therefore Python is slow," but it's not really that accurate.

The established programming wisdom on this subject is to worry about performance once you figure out that performance is actually a problem. If you worry about it when it's not a problem, you'll only make your life more complicated. (Plenty of articles have been written on why "Premature optimization is the root of all evil.")

GLHF! :D

---

### Post by Queue29 on 2010-05-09
> **Portmanteaufu said:**
> 

For most purposes, though, Python is plenty fast. It's understandably easy to get caught thinking that "Python is slower than C, therefore Python is slow," but it's not really that accurate.




You sure about that? Python is pretty damn slow. And a colossal memory hog. 

[http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=gcc](http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=gcc)

---

### Post by Portmanteaufu on 2010-05-09
> **Queue29 said:**
> You sure about that? Python is pretty damn slow. And a colossal memory hog.

I am indeed aware that Python is substantially slower than many languages. My intent was to convey that "Python is slower than <SOME LANGUAGE>" does not mean that "Python is slow." "Python is slow" could mean almost anything.

In my experience, it is never safe to assume that the person posting the question is an expert on anything. It's really easy to form a misconception about a topic (e.g. performance) that follows you for ages. For that reason, I was trying to explain that for a large number of purposes, Python's performance won't be an issue. 

Does Python's print statement take .001 seconds instead of .0001 seconds in your favorite language? You bet! Is that going to matter to someone writing "Hello, World" for their first time? Nah.

When the poster gets to the point where they're writing modules to decode the human genome, they'll probably know enough by then to make a reasonable decision regarding language choice based on their respective performance pros/cons. However, at the moment, (s)he is at the stage where (s)he needs to ask about the difference between compiled and interpreted languages. This suggested to me that I should keep it simple.

I love Python to pieces for of lot of what I do because I seldom have to deal with strict performance requirements. If I did, I'd pick something else.

Mad respect for knowing the benefits and drawbacks of different languages, Queue29. It shows that you know your stuff! :D I just don't want the OP to totally sidestep a great language because there will be better options for certain tasks down the road.

---

### Post by Lex-Man on 2010-05-09
Basically when developing Python I write the code and the first time it's run the virtual machine makes byte code files from my source and then runs that.  

On another topic GTK2.0 is just the latest version of the GTK+ libary?

---

### Post by airtonix on 2010-05-09
> **Lex-Man said:**
> Two quick questions,

Is there a list of the API's that are standard in Ubuntu.  I'm guessing GTK2.

Is there a list of docs like the Java docs for Ubuntu.

Second if Python does not require compiling it does that mean it uses JIT compiling and how does that effect preference of Python programs.
```

sudo apt-get install devhelp python-*-doc 
```

---

