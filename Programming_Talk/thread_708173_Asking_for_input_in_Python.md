---
title: "Asking for input in Python"
date: 2008-02-26
forum: Programming Talk
---

### Post by RedNikon on 2008-02-26
How would I have python ask for user input in a python script. 
For example: 
Have the script ask, "What is your first name?"  > I know this is a string like $A
User inputs, "John"
Later the script could recall, "Please save before exiting, John."

Excuse as this is my first stab at programing.

---

### Post by Martin Witte on 2008-02-26
Answers on these kinda questions are usually found in the tutorials, see eg. [http://docs.python.org/tut/node6.html](http://docs.python.org/tut/node6.html)

---

### Post by ghostdog74 on 2008-02-26
> **RedNikon said:**
> 

Excuse as this is my first stab at programing.
first timers, please read the Python [doc]("http://www.python.org/doc/") and the [tutorial]("http://docs.python.org/tut/"). For the record, raw_input() is what you use to gather input.

---

### Post by Jacks0n on 2008-02-26
```
name = raw_input('What is your first name? ')
print 'Please save before exiting, %s' % name.capitalize()
```

---

### Post by pmasiar on 2008-02-26
If you looked at sticky, we have link to "hello ubuntu in every language" which has examples of exactly this task.

See wiki in my sig for selected links to tutorials for Python beginners and traning tasks.

---

