---
title: "Python error"
date: 2008-12-28
forum: Programming Talk
---

### Post by SonnHalter on 2008-12-28
```
temperature = input(“What is the temperature of the spam?”)

if temperature > 50:
    print “The salad is properly cooked.”
else:
    print “Cook the salad some more.”

```


i get this:temperature = Syntax error: non-ascii character '\xe2' in file txt.py on line 1 but no encoding delared;

---

### Post by catchmeifyoutry on 2008-12-28
Hi, the problem is the type of quotation mark you used in the code.
A string should either be delimited by " or ' characters. You seem to use -fancy- quotation marks that differ left and right of the string, python doesn't support these type of characters (hence the error message).
So if you replace the marks by simple " (so to be exact: Shift+' on most keyboards) the code works.
Probably the problem lies in the editor you used, or some "smart" keyboard setting that automatically replaces the quote characters. Try to use a simple code editor such as gedit, vim, or disable automatic quote replacement somewhere.

---

### Post by SonnHalter on 2008-12-28
it just went away after i retyped it. but it accepts "(" that mark.

---

### Post by catchmeifyoutry on 2008-12-28
Sorry, i don't understand what you mean. Do you now get a different error message about the ( character? Are you running the script with python correctly? Maybe you could post the error here in [CODE] tags ...

---

### Post by SonnHalter on 2008-12-28
i just rewrote the code and it worked.

---

