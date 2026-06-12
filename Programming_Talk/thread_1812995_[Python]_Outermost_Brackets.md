---
title: "[Python] Outermost Brackets"
date: 2011-07-27
forum: Programming Talk
---

### Post by ki4jgt on 2011-07-27
[[a][b]][[a][b][c]]

If you can't tell, there are two sets of outer brackets. How would I place the contents of ONLY the two outermost brackets into a list, or a couple of strings?

---

### Post by NovaAesa on 2011-07-27
I'm having trouble understanding your question. Is "[[a][b]][[a][b][c]]" being input as a string or in a list or what? Could you give an example of input and corresponding output?

---

### Post by MadCow108 on 2011-07-27
you seem to be looking for the flatten operation, which is not available natively in python
the closest thing available I know is itertools.chain.from_iterable:
```
In [3]: [i for i in itertools.chain.from_iterable([[1],["ab"],[3,3]])]
Out[3]: [1, 'ab', 3, 3]
```
[http://docs.python.org/library/itertools.html](http://docs.python.org/library/itertools.html)

---

### Post by Lux Perpetua on 2011-07-27
You do this using a counter: it starts at zero, and every time you see a "[", you increment the counter, and for every "]", you decrement it. 
```

  [ [ a ] [ b ] ] [ [ a ] [ b ] [ c ] ]
0 1 2   1 2   1 0 1 2   1 2   1 2   1 0

```
(Notice that the two pieces you want of the top row are demarcated by the zeros in the bottom row.)

---

### Post by ki4jgt on 2011-07-27
> **Lux Perpetua said:**
> You do this using a counter: it starts at zero, and every time you see a "[", you increment the counter, and for every "]", you decrement it. 
```

  [ [ a ] [ b ] ] [ [ a ] [ b ] [ c ] ]
0 1 2   1 2   1 0 1 2   1 2   1 2   1 0

```
(Notice that the two pieces you want of the top row are demarcated by the zeros in the bottom row.)

I actually thought of this one before I posted this, but I ran into some kind of problem where the going up and coming down intermingled with each other and the entire idea was a fail in my head. I don't exactly know how it went now, so maybe I'll give it another shot.

EDIT: I know it had something to do with the fact that the 1 was on the start bracket and 0 was on the close but anyway.

---

### Post by nvteighen on 2011-07-28
A weird Lisp-ish Python implementation for checking whether brackets are balanced or not:

```


def check_brackets(string, open_bracket = '[', close_bracket = ']'):
    # Yay, Lisp-like Python: recursion and lexical closures in a
    # "named-let"-like idiom!

    def recurse_string_for_brackets(string, counter):
        if (string == "") and (counter == 0):
            return True # Match made in heaven!
        elif (string == "") and (counter != 0):
            return False # Mismatch

        head = string[0]
        tail = string[1:]
        
        if head == open_bracket:
            counter += 1 # Breaking FP-style...
        elif head == close_bracket:
            counter -= 1
        
        return recurse_string_for_brackets(tail, counter)


    return recurse_string_for_brackets(string, 0)

```

EDIT: Great... I completely missed the thread's topic. Forget this post.

---

