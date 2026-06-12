---
title: "[SOLVED] noob python question"
date: 2008-10-07
forum: Programming Talk
---

### Post by T2manner on 2008-10-07
How do i change directories?
i'm trying to test some of of my modules in the terminal, but they aren't in the home folder and i'm not sure how to change directories to get to the module

---

### Post by LaRoza on 2008-10-07
> **T2manner said:**
> How do i change directories?
i'm trying to test some of of my modules in the terminal, but they aren't in the home folder and i'm not sure how to change directories to get to the module

See 6.1.2 [http://www.python.org/doc/2.5.2/tut/node8.html](http://www.python.org/doc/2.5.2/tut/node8.html)

You could also move to the directory they are in before starting Python (cd).

The way to change directories in Python is (but not the solution to this problem) is "os.chdir()".

---

### Post by T2manner on 2008-10-07
I read that, but I couldn't find how to solve my problem.

---

### Post by TreeFinger on 2008-10-07
```
$ sudo apt-get install ipython
$ ipython
```

```
 In [1]: %cd 'dir/here' 
```

---

### Post by T2manner on 2008-10-07
i don't want ipython..
i want to use regular python...

---

### Post by TreeFinger on 2008-10-07
> **T2manner said:**
> i don't want ipython..
i want to use regular python...

You are using 'regular' python. Just a different interpreter. I don't see what the big deal is. Quick solution for your question.

---

### Post by LaRoza on 2008-10-07
> **T2manner said:**
> i don't want ipython..
i want to use regular python...

What is the directory structure of the module? (Absolute paths please).

---

### Post by T2manner on 2008-10-07
the module is in /home/tyler/Code
all i want to do is import the module in terminal without having to change the directory before i start python

---

### Post by LaRoza on 2008-10-07
> **T2manner said:**
> the module is in /home/tyler/Code
all i want to do is import the module in terminal without having to change the directory before i start python

Add this to your code:

```

import sys
sys.path.append('/home/tyler/Code')

```

(Unless "Code" is the module, then use /home/tyler)

---

### Post by T2manner on 2008-10-07
thankyou very much :]

---

