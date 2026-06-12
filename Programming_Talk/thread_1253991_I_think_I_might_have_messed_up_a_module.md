---
title: "I think I might have messed up a module?"
date: 2009-08-30
forum: Programming Talk
---

### Post by filifunk on 2009-08-30
So I've been working on my python skills and messing around with matplotlib.  I was working on some exercises found on a website for matplotlib and decided to name the file 'matplotlib.py'  Which asks, "Enter the number of the exercise: "

I worked on that for a while and opened up a new document called 'plot.py 'just to see if some other matplotlib exercise woule work.   When I open 'plot.py', it runs the 'matplotlib.py' script I have and asks "Enter the number of the exercise"...even though when I check the code of 'plot.py' there is nothing even close to that.

So the computer is somehow going back to matplotlib.py and using that for some reason.  My theory is maybe I had messed up the 'pylab' module so whenever I import it, it somehow goes back to the matplotlib.py script?  How do I fix this?  

=)

---

### Post by filifunk on 2009-08-30
yeah I tried making a new file with just

```

import pylab

```

as the only written code and it does the same thing.  Whenever I import pylab  it asks what the number of the exercise is.  How do I fix this?  I did find a matplotlib.pyc file in my directory.  Should that be there?  Can I delete that or will I lose matplotlib?  Obviously I'm very new to this.

---

### Post by unutbu on 2009-08-30
Rename your personal matplotlib.py and matplotlib.pyc to something else that does not conflict with any other module names and you should be good to go.

When you run a python script, the directory that contains the python script gets added to *the front* of your sys.path. Whenever you import a module, the directories listed in sys.path are searched. Since your personal directory is searched before any of the system's python installation directories, your version of matplotlib.py is getting imported instead of the usual one. The fix is simply not to name any of your scripts the same name as standard module names.

---

### Post by filifunk on 2009-08-30
thanks unutbu!  I hope to help out others when I reach your level!

---

