---
title: "Python: why is this bad syntax?"
date: 2009-08-27
forum: Programming Talk
---

### Post by filifunk on 2009-08-27
Hi all,

I just started learning Python about a week ago.  I was writing this part of a script and got "bad syntax"

bday = raw_input('Have you had your birthday yet (y/n)? ')
if bday == "y":
    bday + 1758
else:
    bday + 1757


^ apparently the second line (if bday =="y") is bad syntax, but why is it?

Thanks!

---

### Post by Mirge on 2009-08-27
> **filifunk said:**
> Hi all,

I just started learning Python about a week ago.  I was writing this part of a script and got "bad syntax"

bday = raw_input('Have you had your birthday yet (y/n)? ')
if bday == "y":
    bday + 1758
else:
    bday + 1757


^ apparently the second line (if bday =="y") is bad syntax, but why is it?

Thanks!

Use [ code ] ... [ /code ] tags please so whitespace is maintained.

Example in Python 3:

```

bday = input("Have you had your birthday yet? (Y/N): ").strip()
if bday.upper() == "Y":
    print("You said yes.")
elif bday.upper() == "N":
    print("You said no.")
else:
    print("WTF!")

```

---

### Post by filifunk on 2009-08-27
thanks, I was wondering how to get that code box.

---

### Post by Mirge on 2009-08-27
> **filifunk said:**
> thanks, I was wondering how to get that code box.

You can paste your code, highlight it (select it)... and click the "#" graphic at the right side of the top menu that has bold, italic, underline, alignment, etc buttons too.

```
This is
     another
example
```

---

### Post by wmcbrine on 2009-08-27
I think your problem is with your third line (and fifth line), not your second:

> **filifunk said:**
> bday + 1758

Two things there: First, you're trying to add an integer to a string. Second, even if that worked -- nothing is being done with the result; it's just discarded. 

However, the first problem would cause a TypeError exception, not "bad syntax". I don't know how that's happening, unless your real code is different from what you've shown.

---

### Post by Bodsda on 2009-08-27
> **filifunk said:**
> Hi all,

I just started learning Python about a week ago.  I was writing this part of a script and got "bad syntax"

bday = raw_input('Have you had your birthday yet (y/n)? ')
if bday == "y":
    bday + 1758
else:
    bday + 1757


^ apparently the second line (if bday =="y") is bad syntax, but why is it?

Thanks!

It's difficult to say. Especially because; as said before, your program raises a TypeError not a Syntax Error. You are trying to perform a mathematical expression with an int upon a string, which wont work.

Also, if you are checking for a lower case 'y' then you should make sure the input is lower case by doing
```

bday = raw_input('Have you had your birthday yet (y/n)? ').lower()

```
Otherwise, if you enter 'Y' then your comparison will return False. 

If you explain what you were trying to do then maybe we can be of some more assistance.

> **wmcbrine said:**
> nothing is being done with the result; it's just discarded.

It's not discarded 'straight' away, it is printed first
```

>>> i = 1
>>> i + 2
3
>>> i
1
>>>

```

Regards,
Bodsda

---

### Post by wmcbrine on 2009-08-27
> **Bodsda said:**
> It's not discarded 'straight' away, it is printed firstOnly if you're working in an interactive shell. He said this was a script.

Anyway, having seen [his other thread](http://ubuntuforums.org/showthread.php?t=1251307), it appears the answer was indeed that his real code was different from what he posted here.

---

