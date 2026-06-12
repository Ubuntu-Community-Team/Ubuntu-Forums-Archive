---
title: "Python 3.x vs Python 2.x"
date: 2011-06-18
forum: Programming Talk
---

### Post by Spiritof76 on 2011-06-18
I've been attempting to learn Python, and I don't know whether I should be concentrating on learning 2.x or 3.x,. They are significantly different that it gets very confusing for me to switch back and forth. It would seem that 3.x is the future and that 2.x would be phased out, although I still see many more new programs on 2.x being developed than 3.x . Python 2.x itself is still being updated. The biggest problem I have with 3.x is that I haven't found many good free tutorials and books. 

As a side issue.  I find that my version of Python is stuck on 3.6 and 3.1 (Ubuntu 10.4.2) Should I attempt to keep this better upgraded? How would I do this.

TIA

---

### Post by simeon87 on 2011-06-18
It doesn't really matter. It's just that many libraries haven't been ported from 2 to 3 yet so you may end up using Python 2 anyway. The differences are not that big if you know Python 2. You can write new projects in Python 3 if you want but many Linux distributions still use Python 2 as default. For convenience, I'd use Python 2 for now.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-18
Yes he is right if u want to work with libraries... i'd recommend Python 2.x....
Python 3.x is of course new but Python 2.x is used almost evrywhre....

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-18
If u want gud buks for python...i'd recommend Sams teach yourself python a bit old buk but simple language...then when u hv finished this buk go for core python programming....

For online tutorials : go to [http://www.pyschools.com/](http://www.pyschools.com/) a gud site to solidify ur basics of the language.... hope this helps

---

### Post by Reiger on 2011-06-18
I would suggest learning Python 3, but use the Python 2.7 interpreter for now. This is based on my subjective experience where Python 2.7 seems to work quite well for mixing & match Python 3 with Python 2 (i.e. your own code written in 3, with the older libraries written in 2.x).

---

### Post by Barrucadu on 2011-06-18
If you learn one, it's pretty easy to pick up the other, so I don't think it really matters which you learn first&#8212;you'll probably end up using Python 3 in the future, anyway.

---

### Post by cgroza on 2011-06-18
Python2 isn't going anywhere in the next 5 years...

---

### Post by Reiger on 2011-06-18
Hmm, judging by the state of CPython it seems quite clear that Python 2.5 is pretty much dead (EOL is set for October 2011), Python 2.6 is fast going the same way (EOL sometime in 2013) which implies quite strongly that Python 2 is going the way of the dodo.

---

### Post by simeon87 on 2011-06-18
> **Reiger said:**
> Hmm, judging by the state of CPython it seems quite clear that Python 2.5 is pretty much dead (EOL is set for October 2011), Python 2.6 is fast going the same way (EOL sometime in 2013) which implies quite strongly that Python 2 is going the way of the dodo.

Yes, but June 2011 - 2013 is a long time to start writing Python 3 software that you can't easily deploy to users. The diferences between Python 2 and Python 3 are not that big; people can start learning Python 2 now and then convert the code to Python 3 in years from now.

---

### Post by oldfred on 2011-06-18
My simple python scripts with only a 100 lines or so have very little difference as I am not calling other libraries.

The only thing I have to change is add the parenthesis  around my print statements that I use to debug variables. 

#!/usr/bin/python3
...
print ("text: ", text)


#!/usr/bin/python
...
print "text: ", text

---

### Post by Spiritof76 on 2011-06-18
The Libraries I would want to use are wxwidgits and curses.

So far the differences, are maddening enough to drive me crazy.. Sorta like going back and forth between windows and MSDOS. Which is why I want to concentrate on one or the other. 

Instinctively one would think that that learning the newest would be the way to go. But 3.x has been around for a couple of years. Still all the programs that come with Ubuntu seem to be 2.x compatible, and there all that much available for tutorials. 

 This morning I found [http://diveintopython3.org/](http://diveintopython3.org/)  I think I will concentrate on 3.1 although I would update to 3.2 if I could figure out how.
 
I do have some doubts that 2.x will ever be replaced by the mainstream

---

### Post by TwoEars on 2011-06-18
My advice is to use 2.x. As far as I am aware, there is currently no native 3.x version of wxwidgets for Python. Most projects are built primarily for 2.x, and quite a lot of those that support 3.x use the 2to3 tool.

---

