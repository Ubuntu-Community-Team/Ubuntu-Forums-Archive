---
title: "Python Terminal Output - OS X"
date: 2010-06-10
forum: Programming Talk
---

### Post by McRat on 2010-06-10
<--Python Newbie v3.1.2

When we execute a program under IDLE, the print statements work fine.
```
print ("\nYou drew the",valuen,"of",suitn,"as your card #",num)
```
yields
> 
You drew the Nine of Clubs as your card # 5

You drew the Three of Hearts as your card # 4

You drew the Two of Hearts as your card # 3

You drew the Jack of Spades as your card # 2

You drew the Three of Hearts as your card # 1

But when we do them in the OS X Launcher, it looks like:

> ('\nYou drew the', 'Seven', 'of', 'Diamonds', 'as your card #', 5)
('\nYou drew the', 'Three', 'of', 'Hearts', 'as your card #', 4)
('\nYou drew the', 'Four', 'of', 'Hearts', 'as your card #', 3)
('\nYou drew the', 'Ace', 'of', 'Hearts', 'as your card #', 2)
('\nYou drew the', 'Four', 'of', 'Diamonds', 'as your card #', 1)
Exit status: 0
logout

[Process completed]


Why does it do this, and how do we fix it?

---

### Post by Bachstelze on 2010-06-10
Python shell or just running the script directly?

---

### Post by McRat on 2010-06-10
> **Bachstelze said:**
> Python shell or just running the script directly?

Top example is running under IDLE.

Messed up one (bottom) is if we use the OS X 3.1.2 Python Launcher, like you would launch a script from Documents.

I guess it's not Terminal.  I'll edit that.

Wait, the "Launcher" just opens up a Terminal Window and executes it.

---

### Post by McRat on 2010-06-10
Nevermind.  It's something in Mac 3.1.2 Launcher doing it.  If I go directly into Terminal and go:

python3 cards1.py

it works like it's supposed to.

My apologies.

---

### Post by Bachstelze on 2010-06-10
Yeah, the Mac launcher uses Python 2, which doesn't like to have several comma-separated expressions in a parenthesised print (you're just giving it a tuple of strings, so it will print it as is). Removing the parentheses and/or the commas will work in Python 2.

---

