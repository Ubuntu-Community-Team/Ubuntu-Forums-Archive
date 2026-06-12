---
title: "Python - Getting bash commands to use pythons variables"
date: 2010-06-22
forum: Programming Talk
---

### Post by Admiral Yi on 2010-06-22
Hello,
I'm learning python, and am currently moving on to creating graphical programs using glade. I though a nice easy starting point would be to create a graphical front end for ls. The interface is all done, but now im stuck on the code. Want I want is for the user to enter some text to search for, then use ls to search for it, like this:

```
import commands

a = str(raw_input("\nEnter keywords: "))

commands.getoutput("ls -l a")
```

Of course, in that example ls just searches for 'a' rather than using the variable I got earlier. So basically, how do I get the ls command to search for the variable 'a' rather than just 'a'?

---

### Post by simeon87 on 2010-06-22
Use string concatenation:

```
import commands

a = str(raw_input("\nEnter keywords: "))

commands.getoutput("ls -l " + a)
```

---

### Post by Admiral Yi on 2010-06-22
Ah, that's so obvious, can't believe I didn't see it. Thank you.

---

