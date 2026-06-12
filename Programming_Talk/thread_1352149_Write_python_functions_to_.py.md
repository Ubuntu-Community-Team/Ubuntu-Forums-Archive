---
title: "Write python functions to .py"
date: 2009-12-11
forum: Programming Talk
---

### Post by HarrisonNapper on 2009-12-11
Anyone know of a reference for writing a function from interactive mode to a file? I read something about pickling that will probably do the trick, but if anyone knows a succint way to accomplish this or any modules that make it easy, that would be helpful.

So, in summary, if I create class 'Class' with function 'function', I want to be able to have something along the lines of:
```

f=open('test.py','r+')
f.write(Class)

#or even

f.write(Class.function())

```

Cheers and thanks in advance for the help. Once I get off of work, I can look it up online, but if you have a few seconds and have a particular method you like, I would appreciate it if you shared. :)

---

### Post by Mickeysofine1972 on 2009-12-11
You can use pickling but I dont think it will serialise your functions, it will only write and restore the data in your objects

```
import pickle

f = open( "my_file", "w" )
c = AClass()
pickle.dump( c, f )
```

to restore:

```
import pickle

f = open( "my_file", "r" )
c = pickle.load(f)
```

Hope that helps

Mike

---

### Post by wmcbrine on 2009-12-11
Yeah, this is one area where Python *isn't* the new BASIC -- no "SAVE" equivalent that I know of.

Probably your best bet is to scroll up, select, and paste it to a file. If it's still in the scroll buffer.

---

### Post by nvteighen on 2009-12-11
Seems not even IPython has this feature :(

---

### Post by HarrisonNapper on 2009-12-11
Thanks for all of your replies; they are greatly appreciated. Perhaps this will be something for me to tackle down the road, as it would be an epic module. I wonder if there are restrictions inherent in the language that prevent this? Anyway, thanks again for all of your(pl) input!

---

### Post by doas777 on 2009-12-11
thats part of why I don't do the interactive thing most of the time

---

### Post by HarrisonNapper on 2009-12-11
> **doas777 said:**
> thats part of why I don't do the interactive thing most of the time

I'm just starting out with the language and, in a real sense, any language, so interactive mode provides an environment where I can play around with the code. See things that work more efficiently or that don't work, test out ideas others have had and see whether their methods work with my code, etc. It's basically a controlled environment for me to isolate blocks of code. Given, it's not even really as efficient as edit/run/edit/run with emacs (which I have at work (Windoze) and at home (Linux)), but it's useful in some situations.

---

### Post by jpkotta on 2009-12-17
You can do this in ipython.

```
In [1]: def foo():
   ...:     print "foo"
   ...:     
   ...:     

```

```
In [10]: save foo 1 # input #1
The following commands were written to file `foo.py`:
def foo():
    print "foo"

```

You can specify lists and ranges of lines.  There is also the **edit** magic command, which is similar.

[http://ipython.scipy.org/doc/rel-0.9.1/html/interactive/reference.html#magic-commands](http://ipython.scipy.org/doc/rel-0.9.1/html/interactive/reference.html#magic-commands)

---

### Post by Can+~ on 2009-12-17
I also found this post in stackoverflow, I forgot to post it:

[http://stackoverflow.com/questions/947810/how-to-save-a-python-interactive-session](http://stackoverflow.com/questions/947810/how-to-save-a-python-interactive-session)

It offers IPython, bPython and reinteract.

---

