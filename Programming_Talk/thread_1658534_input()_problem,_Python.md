---
title: "input() problem, Python"
date: 2011-01-02
forum: Programming Talk
---

### Post by Dara Javaherian on 2011-01-02
Hello all,

I have written a simple program in python:

```
x = raw_input("Enter anything: ")

print x
```

Doesn't get much simpler. It runs fine, but the arrow keys don't work properly:

```
dara@dara-laptop:~/autotxt$ python aaa.py 
Enter anything: Hello there^[[D^[[D^[[D^[[Deheje!!
Hello teheje!!

```

Is there a workaround?

Thank you :)

---

### Post by nice_like_rice on 2011-01-02
You could parse ^[[D or whatever it was as a right arrow key I guess? What did you expect the arrow keys' output to be?


If you want to use arrow keys you should use something like Pygame, or Tkinter I think.

:)

---

### Post by Dara Javaherian on 2011-01-02
> **nice_like_rice said:**
> You could parse ^[[D or whatever it was as a right arrow key I guess? What did you expect the arrow keys' output to be?


If you want to use arrow keys you should use something like Pygame, or Tkinter I think.

:)

I need the file to be run from a command line. I would expect the following:

```

                            v------Cursor
Enter something: Hello There

*left arrow pressed a few times*
                        
                         v------------Cursor
Enter something: Hello There

*something typed in*

Enter something: Hello Theeeeeere

```

Do you know what I mean?

---

### Post by nice_like_rice on 2011-01-02
Yes I know what you mean, and I solved it (woop woop)!

Try this:

```

import readline

test = raw_input("type something in:")

print test

```

Works fine for me. See the man page for raw_input, that's where I figured it out from.

David

---

### Post by Dara Javaherian on 2011-01-02
> **nice_like_rice said:**
> Yes I know what you mean, and I solved it (woop woop)!

Try this:

```

import readline

test = raw_input("type something in:")

print test

```

Works fine for me. See the man page for raw_input, that's where I figured it out from.

David

WAHOO! Thanks a million!

---

