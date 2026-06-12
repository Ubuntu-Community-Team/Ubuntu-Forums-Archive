---
title: "[Python] Begginner question"
date: 2010-08-01
forum: Programming Talk
---

### Post by Antihero20 on 2010-08-01
On this program I'm doing to get myself polished in python I'm trying to use the len() function to display the number of characters of a word, name, etc. bu it doesn't seem to work.  Does the len() function only apply to numbers?

> Fname = raw_input("Please enter your first name: ")
Lname = raw_input("Please enter your last name: ")
print "Your First name has: "  + len(Fname) + " characters"

print "Your Last name has: " + len(Lname) + " characters"

---

### Post by dwhitney67 on 2010-08-01
Try something like:
```

print "Your Name has: ", len(Fname),  " characters."

```
The way you were attempting to do it, you (probably) got an error indicating that you cannot concatenate strings and a number (int).

---

### Post by Antihero20 on 2010-08-01
That worked perfectly, thanks dwhitney

So when I attempt to use strings and a numbers together I should avoid doing it with "+"??

---

### Post by Bachstelze on 2010-08-01
> **Antihero20 said:**
> 
So when I attempt to use strings and a numbers together I should avoid doing it with "+"??

Using + is fine, but only on strings.  len(foo) is an integer, not a string. ;) Alternatively, you can do it printf()-style:

```
print "Your name has %s characters." % len(Fname)
```

---

### Post by Antihero20 on 2010-08-01
Ok I see, thanks

BTW sorry if my questions seem a little vague or don't seem to make a little sense, English is not my language.

---

### Post by trent.josephsen on 2010-08-01
> **Bachstelze said:**
> Using + is fine, but only on strings.  len(foo) is an integer, not a string. ;) Alternatively, you can do it printf()-style:

```
print "Your name has %s characters." % len(Fname)
```

Or by explicitly converting the int to a string first:

```
print "Your name has " + str(len(Fname)) + " characters."
```

None of these solutions is wrong (although I'd lean toward using commas here).  Just use one that works for you.

---

