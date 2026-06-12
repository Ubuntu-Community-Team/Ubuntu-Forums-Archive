---
title: "Python: Where to begin?"
date: 2007-02-23
forum: Programming Talk
---

### Post by Sicilianmandolin on 2007-02-23
I'm very new to programming. The only experience I have programming is through mark-up languages (not programming, I know) and VB.Net. I'm dissatisfied with VB.Net and just about every programmer I've talked to advocates steering clear of it. I've heard that Python is a good introductory language, but I honestly have no clue where to begin. I have no idea what to download or what to use as reference material (save for W3Schools). What can I download through the synaptic manager to get me started, and how do I configure everything appropriately? Please remember that I'm new to Linux, as well.

Thanks for the input in advance!

-Giuseppe

---

### Post by maxamillion on 2007-02-23
[http://docs.python.org/tut/](http://docs.python.org/tut/) <---- good place to start

---

### Post by Wybiral on 2007-02-23
Python doesn't really take any configuration... Open up a text editor and type:

```

print "Hello world!"

```

And save it as "hello.py"

Command line your way over to where you saved it, then enter this in the terminal:

```

python hello.py

```

There you go... That's all you need to do in ubuntu to start programming in python.

Have fun and good luck!

---

### Post by Sicilianmandolin on 2007-02-23
Don't you need anything to make a functional program with a GUI, etc?

---

### Post by tkjacobsen on 2007-02-23
You can use pygtk ([http://www.pygtk.org/](http://www.pygtk.org/)) to create GUIs for your programs. But to begin with, you should just get used to python without making GUIs.


EDIT: pygtk is included in ubuntu

---

### Post by Wybiral on 2007-02-23
Different modules... But python comes pre-installed with a lot of modules. Using the "import" keyword will include these in your program. I suggest hitting the book and learning about the modules you want to use... If you don't have something you want, look for it and install it.

But definitely learn the language itself first, read some python tutorials and get a feel for simple command line in/out and how to manipulate data and program flow.

Stuff like this is important before you worry about GUI's and such...

```

for i in range(10):
   print "This is iteration #", i

```

and...

```

for i in range(10):
   if i == 5:
      print "Behold... The number 5!"
   else:
      print "This is just iteration #", i

```

and...

```

for i in range(4):
   for n in range(4):
      if n == i:
         print n, "==", i
      else:
         print n, "!=", i

```

You know... Get a feel for things first.

After all... What good is being able to program a GUI if you can't make it do stuff?

---

### Post by Sicilianmandolin on 2007-02-23
Well, I'm rather accustomed to VB.Net, where they both go hand-in-hand. This practice of coding first is somewhat foreign to me. I'll give it a try.

---

### Post by kinson on 2007-02-23
> **Wybiral said:**
> Python doesn't really take any configuration... Open up a text editor and type:

```

print "Hello world!"

```

And save it as "hello.py"

Command line your way over to where you saved it, then enter this in the terminal:

```

python hello.py

```

There you go... That's all you need to do in ubuntu to start programming in python.

Have fun and good luck!

I never knew it was that easy to get started :o I've been wanting to try for a while now, but had to focus on C#/C++ for work purposes. Lol, I'll give this a try when I get home tonight :D

Thanks :)

---

### Post by kinson on 2007-02-23
> **Sicilianmandolin said:**
> Well, I'm rather accustomed to VB.Net, where they both go hand-in-hand. This practice of coding first is somewhat foreign to me. I'll give it a try.

Sound a bit like you're coding all the logic into the interface itself(I'm not sure how to say this).

E.g. Coding all the calculations etc into "button1" :/ Code should be separate from the interface. i.e. Button1 calls function1.

Cheers,
Kinson

---

### Post by Sicilianmandolin on 2007-02-23
> **kinson said:**
> Sound a bit like you're coding all the logic into the interface itself(I'm not sure how to say this).

E.g. Coding all the calculations etc into "button1" :/ Code should be separate from the interface. i.e. Button1 calls function1.

Cheers,
Kinson

Essentially, yes, you double-click the object on a graphical form that you've already put together and you're presented with a place to code the conditions for the object. You can download Visual Basic.Net Studio Express from the website free if you'd like. It's a nice language for really simple applications that you'd like pumped out in no time, and for MS Office extensions and such, but that's about it.

---

### Post by kinson on 2007-02-23
> **Sicilianmandolin said:**
> Essentially, yes, you double-click the object on a graphical form that you've already put together and you're presented with a place to code the conditions for the object. You can download Visual Basic.Net Studio Express from the website free if you'd like. It's a nice language for really simple applications that you'd like pumped out in no time, and for MS Office extensions and such, but that's about it.

I understand what you mean. I'm using C# and Visual Studio 2005 at work. :) My point is that you should't code something like "a = 1 + 1" into the button, rather code the button to call a function like add(1,1).

Thats kinda what Wybiral meant by not needing the interface yet. You code the "Add function" I mentioned, and the interface can be done later to just call your "Add Function" :)

Sorry if I'm getting a bit off topic, feel free to ignore this :)

Cheers,
Kinson

---

### Post by geirha on 2007-02-23
instead of running the script with for instance "python hello.py", you can add the following line as the first line of the file:
```
#!/usr/bin/env python
```
which tells bash that the contents of this file should be processed by python.
Then, make it executable by 
```
chmod +x hello.py
```
and run with "./hello.py"

---

### Post by pmasiar on 2007-02-23
> **Sicilianmandolin said:**
> I'm very new to programming. (...) I've heard that Python is a good introductory language, but I honestly have no clue where to begin. 

As you might guess, "how to start programming in X" is FAQ and we have a sticky :-) How to start programming - guides and links for many languages [http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

Python is installed at your Ubuntu box. You may want to install IDE - IDLE is the simplest Python IDE around. 

[http://learnpydia.pbwiki.com/](http://learnpydia.pbwiki.com/) has many links to intro online books about Python, data structures, and training tasks to solve. Enjoy!

---

### Post by dthury on 2007-02-23
In addition to the tutorials at [http://www.python.org]("http://www.python.org") referenced earlier, a couple of "Teach yourself" books I recommend are:
   O'Reilly's _*Learning Python*_  and
   Apress's *_Beginning Python: From Novice to Professional_*

I've used and like both for differing reasons!   From there, let your own interests and needs determine what further books you get.

Have fun!!
   Denny

---

