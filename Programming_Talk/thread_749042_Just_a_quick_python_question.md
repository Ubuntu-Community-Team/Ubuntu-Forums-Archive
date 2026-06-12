---
title: "Just a quick python question"
date: 2008-04-08
forum: Programming Talk
---

### Post by Xavieran on 2008-04-08
I have noticed that when I load a module in my directory it seems to make a copy with a .pyc extension...

Any Idea what this is?
I was thinking that it might be the python code converted to c code but when I catted it it came out as usual...

EDIT:
btw: I have a password input in a little program I am writing that takes it's form like so
[CODE]pass=raw_input("Password")[CODE]
Of course,when it's run anyone can see the password on the screen...
I have heard that the termios module can hide the text but I have no Idea how I could use it...
thanks, xavieran

---

### Post by [h2o] on 2008-04-08
The .pyc are compiled versions of your .py-files. They are generated the first time you run your program, and every time you change the code.

Use the getpass module.

---

### Post by LaRoza on 2008-04-08
> **Xavieran said:**
> I have noticed that when I load a module in my directory it seems to make a copy with a .pyc extension...


It is just byte code. It is more efficient, but is just as cross platform as the regular code.

If you change a module, after importing it, you will see that the changes don't take effect, because the .pyc file is being used. You have to reload the module or delete the .pyc.

---

