---
title: "Python: functions has to be define first in the code to work?"
date: 2007-08-01
forum: Programming Talk
---

### Post by tjansson on 2007-08-01
I probably misunderstood something but as I see it now I need to define a function before a call in Python. This makes sense when thinking of Python as a scripting language - but I am using it as programming language and this problem really makes my code look ugly and confusing. 

Did I misunderstand something or is there really no way around this?

---

### Post by LaRoza on 2007-08-01
That happens in many languages.

To make the code clean, put the function in a different file, then import them.

This also makes them reusable.

---

### Post by EndPerform on 2007-08-01
I think it's a matter of taste, personally.  I like having my functions and classes up top.  To eliminate confusion, just comment your code:

```

import os

# ---- Start Functions ----#

# some_func - A cool function
def some_func():
   print "hi"

# ---- End Functions ---- #

some_func()

```

I do agree, though, if you have code you're going to reuse in other apps, go ahead and move that out to a separate file.

---

### Post by pmasiar on 2007-08-01
> **tjansson said:**
> as I see it now I need to define a function before a call in Python. This makes sense when thinking of Python as a scripting language - but I am using it as programming language and this problem really makes my code look ugly and confusing. 

Not sure how you differentiate between "scripting" and "programming" :-) , and how writing readable code  makes your code ugly. :-)

But order you mentioned is necessary - you wished for fast single-pass source code parser, didn't you? So you got your wish. :-D Be more careful next time.

I hazard to guess you have huge main program with some functions at the end. You can easily convert it to this format:

```

def main():
    sub1()
    sub2()

def sub1():
    # code
def sub2():
    # code

if __name__ == "__main__":
    main()


```
See also [Guido's blog post](http://www.artima.com/weblogs/viewpost.jsp?thread=4829) about writing main() the right way. And trust me, Guido knows what he is talking about :-)

This way, your module will run main() if called as main program, and not run it if imported. You can have your cake and eat it too.

---

### Post by SomethingUniqueHere on 2007-08-01
Functions gotta go first, any procedural code goes at the bottom.  Importing of functions is nice to do but not always practical depending on what they do.  Also, i found this really confusing when i just got into python -

```
if __name__ == "__main__":
    main()
```

That's something you only need if you ever plan on importing this file as a module in another.  It essentially says "if you're running this as a script then execute main" but if you're importing it to another program nothing is going to execute unless explicitly called.

Hope that clears stuff up

---

### Post by pmasiar on 2007-08-01
if doing it flexible and right is confusing, instead of 

```
if __name__ == "__main__":
    main()
```

do just at the last line
```

main()
```

and make sure you do not import that module (because main() would be executed).

---

### Post by tjansson on 2007-08-06
Thanks for the advice guys. :D My problems is that I have a class for some buttons. The buttons have a disable method but I can't disable a given button before I have initiated it - this makes sense off course but It makes the code look bad since I have initiate all the button in top and draw later on. :D

---

### Post by pmasiar on 2007-08-06
wrong. just put all code you have in top (module) level into a main() function, and call this function at last line.

names have to be known only at at execution time - can you post your (simplified) code sample?

---

