---
title: "Is this acceptable? (Python Code)"
date: 2011-05-02
forum: Programming Talk
---

### Post by kevin11951 on 2011-05-02
Is it ok to call a function from within itself?

for example:

[PHP]
def myFunction():
    var = raw_input('Type here: ')

    if var == 'exit':
        break

    else:
        myFunction()
[/PHP]

---

### Post by schauerlich on 2011-05-02
> **kevin11951 said:**
> Is it ok to call a function from within itself?

for example:

[PHP]
def myFunction():
    var = raw_input('Type here: ')

    if var == 'exit':
        break

    else:
        myFunction()
[/PHP]

First of all: i think you mean return there, not break. Break is for inside loops. Otherwise, it's okay in that it's acceptable syntax and will do what you want it to. However, it's wasteful, and in bad form. Whenever you call a function, you have to keep track of where you came from in a data structure called the [call stack](http://en.wikipedia.org/wiki/Call_stack). That means that each time the user doesn't say "exit", you're adding to that call stack. Now, chances are the user isn't going to say the wrong thing a few thousand times and fill up all your memory, but it's still not great form to call a function within itself unless the algorithm you're using is recursive, and simpler than an iterative version. The code you want looks more like this:

```
def myFunc():
    s = ""
    while s != "exit":
           s = raw_input("Say something: ")

```

---

### Post by Arndt on 2011-05-02
> **schauerlich said:**
> First of all: i think you mean return there, not break. Break is for inside loops. Otherwise, it's okay in that it's acceptable syntax and will do what you want it to. However, it's wasteful, and in bad form. Whenever you call a function, you have to keep track of where you came from in a data structure called the [call stack](http://en.wikipedia.org/wiki/Call_stack). That means that each time the user doesn't say "exit", you're adding to that call stack. Now, chances are the user isn't going to say the wrong thing a few thousand times and fill up all your memory, but it's still not great form to call a function within itself unless the algorithm you're using is recursive, and simpler than an iterative version. The code you want looks more like this:

```
def myFunc():
    s = ""
    while s != "exit":
           s = raw_input("Say something: ")

```

The above is correct (unlike in some languages like Erlang, where the OP's proposed recursive construction is the only way to implement loops), but there is a place for recursive functions (meaning functions that call themselves directly or indirectly) in Python too. I don't know what limits Python imposes, but for traversing a binary tree, for example, I would use recursion.

---

### Post by NovaAesa on 2011-05-02
What you have there is tail recursion, because the recursive call is returned straight away. Normally this sort of construct is fine when programming, but Python doesn't have tail call elimination (please correct me if I'm wrong) and thus it's best to avoid in Python.

---

### Post by schauerlich on 2011-05-02
> **Arndt said:**
> but there is a place for recursive functions (meaning functions that call themselves directly or indirectly) in Python too.

Right - but this isn't haskell, there's no reason to use recursion in place of a simple while loop. It's unnecessary and I would argue less clear.

> I don't know what limits Python imposes, but for traversing a binary tree, for example, I would use recursion.

Again, there are plenty of legitimate uses for recursion, depending on what language you're using and what you're trying to accomplish. I'm a fan of [functional programming](http://en.wikipedia.org/wiki/Functional_programming) - I'm in no way afraid of recursion. :) It simply has its time and place in imperative languages, and this is not one such instance.

---

### Post by lukeiamyourfather on 2011-05-02
> **kevin11951 said:**
> Is it ok to call a function from within itself?

for example:

[PHP]
def myFunction():
    var = raw_input('Type here: ')

    if var == 'exit':
        break

    else:
        myFunction()
[/PHP]

What they mean to say is calling a function within itself is not pythonic.

[http://en.wikipedia.org/wiki/Python_(programming_language)#Name_and_neologisms](http://en.wikipedia.org/wiki/Python_(programming_language)#Name_and_neologisms)

There are better ways to do it (already mentioned) but all are "correct" in the literal sense.

---

### Post by Arndt on 2011-05-03
> **schauerlich said:**
> Right - but this isn't haskell, there's no reason to use recursion in place of a simple while loop. It's unnecessary and I would argue less clear.



Again, there are plenty of legitimate uses for recursion, depending on what language you're using and what you're trying to accomplish. I'm a fan of [functional programming](http://en.wikipedia.org/wiki/Functional_programming) - I'm in no way afraid of recursion. :) It simply has its time and place in imperative languages, and this is not one such instance.

The original question was whether it was ok to call a function from within itself, and provided one particular example. We have established the answer by now, and your post only adds confusion.

---

### Post by simeon87 on 2011-05-03
> **lukeiamyourfather said:**
> What they mean to say is calling a function within itself is not pythonic.

[http://en.wikipedia.org/wiki/Python_(programming_language)#Name_and_neologisms](http://en.wikipedia.org/wiki/Python_(programming_language)#Name_and_neologisms)

There are better ways to do it (already mentioned) but all are "correct" in the literal sense.

Recursion does have its place in Python, it's just that in this case it seems unnecessary. We're not dealing with a recursive data structure such a tree, to name a thing.

---

### Post by StephenF on 2011-05-03
> **simeon87 said:**
> Recursion does have its place in Python, it's just that in this case it seems unnecessary. We're not dealing with a recursive data structure such a tree, to name a thing.
Indeed. You can use recursion to peel the layers from a piece of data so that you can process the innermost layer first. I give you a practical example.
```

import os

def mkdir_p(path):
    """Equivalent to the shell command: mkdir -p path."""
    
    def inner(path):
        if path == os.path.sep:
            return

        head, tail = os.path.split(path)
        inner(head)

        try:
            os.mkdir(head)
        except OSError as e:
            if e.errno != os.errno.EEXIST:
                raise

    if not os.path.isdir(path):
        inner(path.rstrip(os.path.sep))  # Make the parents.
        os.mkdir(path)

```
The directories need to be made in the order, root first and the code in this example provides a last in first out mechanism (LIFO).

LIFO can be achieved in python using the append and pop(0) methods of a list producing rather different looking code to what you see above.

---

