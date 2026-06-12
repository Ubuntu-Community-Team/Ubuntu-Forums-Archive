---
title: "Python Popen freezes GUI"
date: 2007-08-29
forum: Programming Talk
---

### Post by Nekiruhs on 2007-08-29
Ok, heres my issue. I'm writing a search-bar style program ala [Launchy]("http://www.launchy.net/#screenshots"). I don't see a great need to implement another search system so I latched on to the find command to do the dirty work for me. I've been using os.popen() to call find with the search text and to get the results. I've noticed that while find is being called my GUI is completely unresponsive, although find is only using 5% of my processor. Is there some other way to call find that would prevent this? Or is this just one of the things I have to accept if I don't want to reinvent the wheel?

Maybe the subprocess module? How would I use it?

Also, how would I make a gtkProgressBar just move back and forth? I have activity mode checked in glade, but when I call progress.pulse() it just moves a little bit. I want it to show that work is being done, but I cant measure how long it will take.

Thanks.

---

### Post by Nekiruhs on 2007-08-30
No Ideas? Any help? Maybe threading in python is in order? I have no idea how to do that or if it would even help.

---

### Post by christhemonkey on 2007-08-30
What is happening is the GUI is waiting for the os.popen process to finish before it responds.

I think the way to go with this would be to look at the module Threading.

Or another thing you can do (though its a bit of a hack around) is to do something like this:
```
while gtk.events_pending():

    gtk.main_iteration(False)
```


EDIT:

If you read the Pygtk docs, it says a little bit about the pulse() function:
> The pulse() method nudges the progressbar to indicate that some progress has been made, but you don't know how much. This method also changes progress bar mode to "activity mode," where a block bounces back and forth. Each call to the pulse() method causes the block to move by a little bit (the amount of movement per pulse is determined by the set_pulse_step() method).
See here:[http://www.pygtk.org/docs/pygtk/class-gtkprogressbar.html#method-gtkprogressbar--pulse](http://www.pygtk.org/docs/pygtk/class-gtkprogressbar.html#method-gtkprogressbar--pulse)

---

### Post by Nekiruhs on 2007-08-30
Where would I put the lines that you gave me? Or can you link to any good tutorial that covers threading?

---

### Post by nanotube on 2007-08-30
> **Nekiruhs said:**
> Where would I put the lines that you gave me? Or can you link to any good tutorial that covers threading?

well, this here's the python doc for the threading module:
[http://docs.python.org/lib/module-threading.html](http://docs.python.org/lib/module-threading.html)

if that's not enough, you can also find actual walkthrough tutorials with a web search.

---

### Post by loell on 2007-08-30
have you considered threading?

[http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/]("http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/")

edit -- beaten ;)

---

### Post by christhemonkey on 2007-08-30
You can put those lines before any GUI bits of your program, though as i said its a bit of  a hack around.

There are many many howtos on threading.
This pdf helped me understand the concepts (though its a presentation so obviously is lacking the person explaining each bullet point...):
[http://www.strakt.com/docs/eup02_threads_jacob.pdf](http://www.strakt.com/docs/eup02_threads_jacob.pdf)

But just google, python thread how to and read one of the many.

If and when you do find your solution, please post back how you did it.

---

### Post by oOJINxOo on 2007-08-30
although there's better options as stated above.
I just thought i'd mention this anyway
have you tried running it as a background process, pipe the output into a txtfile and then read from that textfile?

good luck whatever method you end up using

<3 the py

---

### Post by scooper on 2007-08-30
Why not just separate it into two programs that share a database, or use the slocate database?  I wouldn't think you need to run find very often, just after stuff is installed.  You could spawn an independent sub-process (not a thread) that rebuilds the database in the background and then swaps it in place as an atomic operation when the search completes.  Or there might be a way to parse /var/lib/slocate/slocate.db, except it needs root access.

I also don't find it very hard to write code to recursively find files directly in Python, i.e. without spawning find.  Here's a simple example.

```
import os.path
import glob

def find(dir):
    for name in glob.glob(os.path.join(dir, '*')):
        if os.path.isdir(name):
            for name2 in find(name):
                yield name2
        else:
            yield name

for name in find('/more/doc'):
    print name

```

Here's a more elaborate example that optionally filters on regular expressions.

```
import os.path
import re
import glob

def find(dir, includes = [], excludes = []):
    for name in glob.glob(os.path.join(dir, '*')):
        if os.path.isdir(name):
            for name2 in find(name, includes, excludes):
                yield name2
        else:
            for reInclude in includes:
                if reInclude.search(name):
                    break
            else:
                if includes:
                    continue
            for reExclude in excludes:
                if reExclude.search(name):
                    break
            else:
                yield name

for name in find('/more/doc', includes = [re.compile('[.]xls$')]):
    print name

```

Obviously there's room for improvement, but just showing how easy it is.  A benefit is that once you control the iteration of files internally you can poll the GUI to keep things alive.  Does that make sense?

---

### Post by Zootropo on 2007-08-30
Threads are the way to go. Just create a class which extends threading.Thread and write the code for the other thread in the run method of this class.

Then you instantiate the class and call the start method.

---

### Post by Nekiruhs on 2007-08-30
> **scooper said:**
> Why not just separate it into two programs that share a database, or use the slocate database?  I wouldn't think you need to run find very often, just after stuff is installed.  You could spawn an independent sub-process (not a thread) that rebuilds the database in the background and then swaps it in place as an atomic operation when the search completes.  Or there might be a way to parse /var/lib/slocate/slocate.db, except it needs root access.

I also don't find it very hard to write code to recursively find files directly in Python, i.e. without spawning find.  Here's a simple example.

Obviously there's room for improvement, but just showing how easy it is.  A benefit is that once you control the iteration of files internally you can poll the GUI to keep things alive.  Does that make sense?
Find isn't something I made, Its a program installed by default on every Ubuntu and most Linuxes. And its not like locate, where it generates a index, it polls the filesystem every time you call it. So I would need to call find each and every time I did a search.

---

