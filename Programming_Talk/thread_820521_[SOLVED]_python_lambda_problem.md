---
title: "[SOLVED] python: lambda problem"
date: 2008-06-06
forum: Programming Talk
---

### Post by Flimm on 2008-06-06
Why won't this code work?

[PHP]#!/usr/bin/env python

if __name__ == "__main__":
    my_list = ["l0", "l1", "l2"]
    functions = []

    for item in my_list:
        functions.append(lambda: item)
    
    # this prints l2 l2 l2, how can I make it print l0 l1 l2?
    print functions[0](), functions[1](), functions[2]()

[/PHP]

How can I make the lambda function save item's value?

---

### Post by CptPicard on 2008-06-06
*Forget what I said here at first, it was nonsense...*

...


I think the reason why it doesn't work is that Python's lambdas are not real closures so you can't capture values like that.

---

### Post by fred.reichbier on 2008-06-06
Hello,

it works with an optional argument with a default value which is the desired value (ouch. understandable?):

```
for item in my_list:
    functions.append(lambda item=item: item)

```

But that's not really nice :D

---

### Post by Flimm on 2008-06-06
Actually, I think I've found a solution:

[PHP]#!/usr/bin/env python

if __name__ == "__main__":
    my_list = ["l0", "l1", "l2"]
    functions = []

    for item in my_list:
        exec "functions.append(lambda: \"%s\")" % item
    
    # this now prints l0 l1 l2
    print functions[0](), functions[1](), functions[2]()

[/PHP]
I don't think this is the best solution though.

---

### Post by Flimm on 2008-06-06
> **fred.reichbier said:**
> Hello,

it works with an optional argument with a default value which is the desired value (ouch. understandable?):

```
for item in my_list:
    functions.append(lambda item=item: item)

```

But that's not really nice :D
Wow, thanks for that. It almost makes sense.
Is this a bad hack, or is this an official way to do it? In other words, is it likely to stop working in future python versions?
Actually, strike that, I think I remember reading that python 3000 will drop support for lambda altogethor.

---

### Post by fred.reichbier on 2008-06-06
Hello,

I haven't heard anything about dropping lambda support in Python 3000, but maybe you're right anyway ;) That is (imho) not perfect coding style, but not a hack, and sometimes useful. 
It's just a lambda with one argument which has a default value. The following would look less like a hack: 
```
lambda blah=item: blah
``` :D
So I suggest it will work in Py3K if it supports lambdas ;)

Greetings,

Fred

---

### Post by pointone on 2008-06-06
[quote=http://www.python.org/dev/peps/pep-3099/]At one point lambda was slated for removal in Python 3000. Unfortunately no one was able to come up with a better way of providing anonymous functions. And so lambda is here to stay.[/quote]

:o

---

### Post by fred.reichbier on 2008-06-06
Good to know, thanks :D

---

### Post by days_of_ruin on 2008-06-06
And even if they did it would be in the functools module they are making,
which is going probably going to have map and reduce in it.

---

### Post by Can+~ on 2008-06-06
But why are you creating a list of functions that just return the value? I don't see any benefit from that approach.

---

### Post by Flimm on 2008-06-06
> **Can+~ said:**
> But why are you creating a list of functions that just return the value? I don't see any benefit from that approach.
I'm not :D It's just a simplified version of the problem I was facing.
What I really wanted to do was to connect several gtk CellRenderers of several TreeView widgets to just one function, passing which TreeView as an argument.
Like this:
[php]cell_renderer[which_tree_view].connect("toggled", lambda cell, path, which_tree_view=which_tree_view: self.customise_toggled(cell, path, which_tree_view))[/php]
Come to think of it, I could have just done:
[php]cell_renderer[which_tree_view].connect("toggled", self.customise_toggled, which_tree_view)[/php]
*slaps himself on the forehead*

---

### Post by pmasiar on 2008-06-06
another cool way to create a function which manipulates another function in some consistent way is [decorator](http://www.ibm.com/developerworks/linux/library/l-cpdecor.html)

---

