---
title: "Python + Emacs"
date: 2008-04-10
forum: Programming Talk
---

### Post by ankursethi on 2008-04-10
I need a bit of help with the Emacs python-mode.

When I write a Python script using Emacs and execute it, bingo! It works. But after the script is done, it leaves all the variables from the execution hanging behind in the inferior Python interpreter. So if I change my script to use different variables, or to use the same variables for different jobs, havoc ensues. The namespace literally gets mutilated.

Is there a way to reload the interpreter each time I execute the script? I can obviously kill the interpreter *manually* each time a script finishes executing but if I was into doing things manually I wouldn't be using Emacs in the first place.

WARNING : I'm an En00b. No knowledge of elisp.

---

### Post by lnostdal on 2008-04-10
right .. you're missing the point of interactive programming

you _want_ to treat the python session as a, well, session .. or a state machine

what you need to do to avoid clutter is to put your code and your "stuff" into a namespace of some sort .. or make sure your state gets reset when you re-evaluate the buffer .. or put your code inside a function and execute that from the repl

..i don't know python, so i do not know exactly how to do this in python - but i do know other interactive languages very well and i'm positive that you will be missing out big time if you don't "adjust" to an interactive programming-type state of mind

edit:
this might _seem_ like extra effort for only scraps in return .. but you'll get it eventually ..

---

### Post by LaRoza on 2008-04-10
> **lnostdal said:**
> right .. you're missing the point of interactive programming

you _want_ to threat the python session as a, well, session .. or a state machine


I hope you meant "treat"...

---

### Post by lnostdal on 2008-04-10
hehe, yes .. x) .. fixed .. thanks!

---

### Post by ankursethi on 2008-04-10
Guess you do have a point there. I did manage pretty well when I was trying out Lisp (never went further than defun, though).

I think I'll stick everything in a function and call that all the time (although it can be frustrating to have several functions when all you want to write is a 30 line throw-away script for getting a webpage). Once the function exits all the variables are bound to go out of scope anyway (does Python have static variables? I don't know ...).

Thanks all the same.

---

### Post by lnostdal on 2008-04-10
include a call to that function (edit: or the functions? .. i don't know exactly how you layout this thing) in the buffer/file .. that way you don't have to call the function manually each time

---

