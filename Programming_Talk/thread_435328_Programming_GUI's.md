---
title: "Programming GUI's"
date: 2007-05-06
forum: Programming Talk
---

### Post by wiebers10 on 2007-05-06
I know this is a simple question but I was going to see what the correct way to do this is.  When you are going to create a program from scratch that is going to have an GUI would it be best to write it all so you could run it from command line first and then make a GUI for all that code or should I just code it using a GUI programming language or GUI IDE.  I am going to program it in Python if that matters at all.

---

### Post by Tomosaur on 2007-05-06
Depends on how you program really. many open-source applications (but not limited to open source!) prefer a modular design, which can mean that the core functionality doesn't depend on the GUI being present.

A modular design can help you write clean code, and makes maintaining the code easier.

It's just a matter of preference really. I would advise you do it, but it's not absolutely necessary.

---

### Post by forsaken_pariah on 2007-05-06
I think tomosaur's on the right track. Make your programs as modular as you can. Not only is it good programming practice, your program could eventually end up evolving into something you never imagined.

"One of Linus's earlier  projects was a program that would switch between printing AAAA and BBBB.  This later evolved to Linux." (Larry Greenfield, *The Linux Users' Guide* Beta Version 1)

---

### Post by cwaldbieser on 2007-05-07
> **wiebers10 said:**
> I know this is a simple question but I was going to see what the correct way to do this is.  When you are going to create a program from scratch that is going to have an GUI would it be best to write it all so you could run it from command line first and then make a GUI for all that code or should I just code it using a GUI programming language or GUI IDE.  I am going to program it in Python if that matters at all.

In python, it is not too hard to design your program as both a module and a command line program.  Something like:
```

def run_program(x,y,z):
    #Do stuff

def another_useful_function(x):
    #Do other stuff

...

if __name__ == "__main__":
    #Do command line processing
   ...
   run_program(1,2,3)

```

Now you have a fully working command line program and a useful library.  Later, when you want to add a GUI:

```

#A simple GUI for myprog.py using Tkinter|PyQt|wxWindows|other.

import myprog

#GUI code with event handlers that eventually call myprog.run_program(x,y,z), etc.

```

---

