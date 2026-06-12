---
title: "[SOLVED] Learning C++"
date: 2008-08-10
forum: Programming Talk
---

### Post by rocknzen on 2008-08-10
I am taking on the challenge of learning C++. There is a lot more that I would like to do with my Pc than just surfing and playing games (work gets boring).

Can someone recommend a good compiler, keeping in mind that this is the first language that I will be learning. So ideally I would like to have something that might be intuitive and have good documentation.

Any other suggestions would be welcomed.

---

### Post by overdrank on 2008-08-10
Moved :)

---

### Post by mssever on 2008-08-10
See the sticky in this sub-forum. Oh, and consider some other language as your first language. Like Python.

---

### Post by LaRoza on 2008-08-10
> **rocknzen said:**
> I am taking on the challenge of learning C++.
That is a challenge...

> 
Can someone recommend a good compiler, keeping in mind that this is the first language that I will be learning. So ideally I would like to have something that might be intuitive and have good documentation.
See sticky for compiler. If you are thinking of an editor, see the sticky for that also (gedit, which comes with Ubuntu is probably the easiest to use)

> 
Any other suggestions would be welcomed.

Read the sticky.

C and C++ are two totally different languages. Writing C and writing C++ is very different. Learning one before the other won't help. You can use C++ like you use C sometimes, but that is discouraged in C++ programming.

---

### Post by pmasiar on 2008-08-10
Experiments (on students in hight school) shown that learning Python before Java improved understanding Java substantially. So I would also recommend you to learn much simpler beginner-friendly language with high-level concepts, before you embark on learning tricky, demanding language where many task done for you by Python you have to do yourself (and do it right, or face problems).

First, learn Python without OOP. Second, learn OOP with Python. Then, learn C, to understand how metal works on low level. Only after then you are ready to tackle C++, which mixes high-level concepts and low-level obsession with efectiveness into a deadly brew.

See wiki in my sig (also in sticky FAQ - read the discussion there for context).

---

### Post by rocknzen on 2008-08-10
What types of things can I create using Python??

Are Python compilers readily available? Easy to use and learn? etc...

---

### Post by NovaAesa on 2008-08-10
You can create almost anything with Python (application programming wise anyway, don't bother trying to write a hardware driver in python). On Ubuntu there is a Python compiler installed by default. Just type:
```

python $script.py

```
into the terminal, replacing $script.py with what your script is actually called.

---

### Post by mssever on 2008-08-10
> **rocknzen said:**
> What types of things can I create using Python??
Anything within your skill level, and much more.
> Are Python compilers readily available? Easy to use and learn? etc...
AFAIK, every mainstream Linux distro (including Ubuntu) includes Python by default. Plus, Python is available for MacOS and Windows. Type python at a prompt and you'll be able to explore.

---

### Post by lisati on 2008-08-10
Although C++ started as an extension to C, it shouldn't be necessary to learn one before the other.

---

### Post by LaRoza on 2008-08-10
> **mssever said:**
> Anything within your skill level, and much more.

AFAIK, every mainstream Linux distro (including Ubuntu) includes Python by default. Plus, Python is available for MacOS and Windows. Type python at a prompt and you'll be able to explore.

OS X has Python by default, and HP and Compaqs have it as well.

> **rocknzen said:**
> What types of things can I create using Python??

Are Python compilers readily available? Easy to use and learn? etc...

You can do a lot with Python. You can make simple scripts, you can make simple or complex GUI's, you can make 2d and 3d games. The Ubuntu graphical installer is written in Python for example and my system restore program is in Python.

---

### Post by nvteighen on 2008-08-11
Python is not compiled (at least in the traditional sense). You just run the script through the Python interpreter.

You create a .py file in your favorite text editor and then use the command "python file.py" to run it.

But the best feature Python has is its interactive shell, where you can test commands and code without having to create a file. Just type "python" in the Terminal for that

EDIT: I voted "Yes, but not necessary" in the poll. C and C++ are different languages, but a good base in C is always a good thing to have, no matter of you later use it in a daily base or not.

---

### Post by pmasiar on 2008-08-11
> **nvteighen said:**
> Python is not compiled (at least in the traditional sense). You just run the script through the Python interpreter.


You cannot say this to kids - kids all want compiled languages! :-)

In fact, Python **is** automagically compiled to .pyc file (and you can distribute pyc files instead of py sources) relevant .py file was changed after .pyc was created. So unlike Perl, you do not have to parse source for every run of the program. It is compiled behind the scenes.

The difference you maybe wanted to point out is that Python is dynamically typed (unlike statically typed C and C++), and lots of work checked statically by traditional compilers is done dynamically at runtime. It soaks out some 20% of performance, but adds 1000% flexibility and developer's productivity, so it is a trade worth to take.

---

### Post by NovaAesa on 2008-08-11
> **pmasiar said:**
> It soaks out some 20% of performance, but adds 1000% flexibility and developer's productivity, so it is a trade worth to take.
Don't forget that data typing bugs can only be found at runtime though, rather that compile time. I much prefer to have the compiler find these for me rather than having to work out where a tiny bug is somewhere.

---

### Post by nvteighen on 2008-08-11
> **pmasiar said:**
> You cannot say this to kids - kids all want compiled languages! :-)

I know... *sigh*... For some people, compilers are almost as "magical" as pointers.

> In fact, Python **is** automagically compiled to .pyc file (and you can distribute pyc files instead of py sources) relevant .py file was changed after .pyc was created. So unlike Perl, you do not have to parse source for every run of the program. It is compiled behind the scenes.

The difference you maybe wanted to point out is that Python is dynamically typed (unlike statically typed C and C++), and lots of work checked statically by traditional compilers is done dynamically at runtime. It soaks out some 20% of performance, but adds 1000% flexibility and developer's productivity, so it is a trade worth to take.

I wanted the OP to understand that he shouldn't look after a compiler like g++ (as he was asking) for Python. That's what I wanted to say with "not compiled (at least in the traditional sense)". Maybe my wording wasn't accurate enough?

But anyway, thanks for clarifying my post. Hopefully the OP gets a better image of what Python offers.

---

### Post by pmasiar on 2008-08-11
> **NovaAesa said:**
> Don't forget that data typing bugs can only be found at runtime though, rather that compile time. I much prefer to have the compiler find these for me rather than having to work out where a tiny bug is somewhere.

Well, if you did your unit testing properly, you would find all those "bad type" bugs at unit testing stage. So, instead for asking for shackles and crutches of static typing, do the testing (what you need to do anyway - you don't do testing? oh the horror!), and you will have all the flexibility and none of the problems.

Best practices are called so for a reason, and you ignore them on your own risk and pain.

---

### Post by stchman on 2008-08-11
> **rocknzen said:**
> I am taking on the challenge of learning C++. There is a lot more that I would like to do with my Pc than just surfing and playing games (work gets boring).

Can someone recommend a good compiler, keeping in mind that this is the first language that I will be learning. So ideally I would like to have something that might be intuitive and have good documentation.

Any other suggestions would be welcomed.

Ubuntu has both a C and C++ compiler (gcc and g++).  There are also IDEs like eclipse and ajunta.

---

### Post by indecisive on 2008-08-15
Go to python.  It's the best.  You will not regret your decision.  What might take 5 minutes in C++ can probably be done in 10 second in python.

---

### Post by slavik on 2008-08-15
> **pmasiar said:**
> You cannot say this to kids - kids all want compiled languages! :-)

In fact, Python **is** automagically compiled to .pyc file (and you can distribute pyc files instead of py sources) relevant .py file was changed after .pyc was created. So unlike Perl, you do not have to parse source for every run of the program. It is compiled behind the scenes.

The difference you maybe wanted to point out is that Python is dynamically typed (unlike statically typed C and C++), and lots of work checked statically by traditional compilers is done dynamically at runtime. It soaks out some 20% of performance, but adds 1000% flexibility and developer's productivity, so it is a trade worth to take.
once again:

perl -MO=Bytecode,-o file.plc file.pl

---

### Post by rocknzen on 2008-08-15
I would like to thank everyone for contributing to this discussion. So it seems to me the consensus is to learn Python first, which would aid in understanding Java as well as others. 


So I think I am going to dive in and officially announce that I am going to learn the computer language called Python.

Look for future posts from me concerning this subject as I may have questions and problems that I am going to need help with.

(that is if you are interested) 

Again thank you all for your comments.


P.S. Feel free to PM me about it.

---

