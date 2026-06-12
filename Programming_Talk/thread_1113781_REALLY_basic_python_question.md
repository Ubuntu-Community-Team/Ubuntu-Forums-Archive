---
title: "REALLY basic python question"
date: 2009-04-02
forum: Programming Talk
---

### Post by Sarai the Geek on 2009-04-02
I woke up this morning and decided that I need to learn to program. I'm not one of those people who goes to the store and picks up a book that says something like "Learn String Theory in Five Seconds!" (yes, I know string theory is *so* three years ago), I'm a learn by fiddling type of person.

I finished my first bona fide program, a really simple tool that calculates the hypotenuse of a triangle based on the length of the legs (it's pythagorean in python). However, I seem to be having trouble with the "if" command. Here's my code:

```

from time import sleep

print "Hello There"
sleep(10)
nuke = input("Would You Like to Nuke Russia? [y/n] ")
if nuke == y
    print "Of course you do! Arming missiles now."
else
    print "Geez, you're a snoozefest."
```

Looking at examples of the if function in code from various sources online, this looks okay. But I keep getting this when I try to run it:
```
sarai@Sarai-Laptop:~/Desktop$ python russia.py
  File "russia.py", line 6
    if nuke == y
               ^
SyntaxError: invalid syntax

```

Can someone please tell me what I'm doing wrong?

---

### Post by WW on 2009-04-02
Put quotes around a literal string, and don't forget the colon:
```

    if nuke == "y":

```
Also, for inputting a string, use **raw_input** instead of **input**.
```

from time import sleep

print "Hello There"
sleep(10)
nuke = raw_input("Would You Like to Nuke Russia? [y/n] ")
if nuke == "y":
    print "Of course you do! Arming missiles now."
else:
    print "Geez, you're a snoozefest."

```

---

### Post by Sarai the Geek on 2009-04-02
> **WW said:**
> Also, for inputting a string, use **raw_input** instead of **input**.


Okay, got it. Do you mind if I ask what the difference is?

---

### Post by WW on 2009-04-02
raw_input() reads characters into a string.  The optional prompt argument is printed first before reading the characters.

input() is equivalent to eval(raw_input()).  In other words, it reads the the string, and then (tries to) evaluate it as a python statement.  If you used input() in your program, and you entered the single character 'y' and hit enter, python would try to evaluate the string 'y', and since the variable y is not defined, you would get an error.

Google for "python raw_input input" and you'll find longer discussions in the first few hits.

---

### Post by Sarai the Geek on 2009-04-02
> **WW said:**
> raw_input() reads characters into a string.  The optional prompt argument is printed first before reading the characters.

input() is equivalent to eval(raw_input()).  In other words, it reads the the string, and then (tries to) evaluate it as a python statement.  If you used input() in your program, and you entered the single character 'y' and hit enter, python would try to evaluate the string 'y', and since the variable y is not defined, you would get an error.

Google for "python raw_input input" and you'll find longer discussions in the first few hits.

That makes sense! Thank you so much!

---

