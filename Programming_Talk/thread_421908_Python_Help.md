---
title: "Python Help"
date: 2007-04-24
forum: Programming Talk
---

### Post by tux_rox on 2007-04-24
So I saw that a lot of stuff in Ubuntu is based in Python, so I decided to give it a try.  I haven't done any programming on the computer before; I am, however, experienced with programing in TI-BASIC (the language on Texas Instruments graphing calculators).

So far, it all makes sense; the only problem is, I don't know how to indent a second line correctly.

For example:

CODE

temperature = input(“What is the temperature of the spam?”)

if temperature > 50:
    print “The salad is properly cooked.”
else:
    print “Cook the salad some more.”

How do I first indent the "print" commands, and how do I type the "else" without running the "if" statement?

Thanks for any help - if I get good enough, might try doing some Google Summer of Code (yeah, right)

---

### Post by raja on 2007-04-24
It is not clear what your question is exactly. Both the print statements must be indented one level, while the if and else statements will remain unindented. Is that what you wanted to know?

---

### Post by tux_rox on 2007-04-24
Sorry - it's simpler than it sounds.  How do I indent the print statements?

(Yeah, I know it's basic, but I can't do much without it!)

---

### Post by raja on 2007-04-24
O.K. I think I know what you are asking. Indentation has to be some constant amount of white space. So it can be one space even - though more usually it is about 4 spaces. Typically, an editor will indent with a predefined whitespace for you automatically.

---

### Post by tux_rox on 2007-04-24
I did a little experimenting and now everything works - thank you!

:guitar:

---

### Post by WW on 2007-04-24
You can preserve the indenting in your code samples in the forum by enclosing the code in [ code ] and [ /code ] tags (but don't put any spaces inside the brackets).

Here is how your example should be indented:
```

temperature = input("What is the temperature of the spam? ")

if temperature > 50:
    print "The salad is properly cooked."
else:
    print "Cook the salad some more."

```
I'll call the file example.py, and run it a few times:
```

$ python example.py
What is the temperature of the spam? 38
Cook the salad some more.
$ python example.py
What is the temperature of the spam? 99
The salad is properly cooked.
$

```

EDIT: Heh, you're too quick... you had it all figured out before I could finish responding.

---

### Post by pmasiar on 2007-04-24
Python is good choice, especially for beginner. Check links in sticky and in my sig. Make sure stat you are using decent (programming) editor, at least IDLE, or SPE. If you mix tabs and spaces, strange confusing bugs will happen.

To do nothing, use "empty" statement: pass, like:

```

if 1 == 2:
    pass
else:
    print 'here we go'

```

---

### Post by deathbyswiftwind on 2007-04-24
You should use idle. It does the indents for you automatically. Its right in the repos

```

sudo apt-get install idle-python2.5

```

---

