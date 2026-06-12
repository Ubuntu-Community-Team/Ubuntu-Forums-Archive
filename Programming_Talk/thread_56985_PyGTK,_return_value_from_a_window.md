---
title: "PyGTK, return value from a window?"
date: 2005-08-14
forum: Programming Talk
---

### Post by Nequeo on 2005-08-14
Greetings all,

I've been working through the PyGTK tutorial, and haven't had any problems as far as creating a user interface is concerned. But there is one thing I have not been able to find, or figure out. 

Basically, I have a class: AddAccountWindow. Which is basically a factory class with a GUI attached. The window asks for the usual information. Account type, username, password, host, etc... Then when they hit 'okay', it generates a new class instance (of a different type), AddAccountWindow.new_account.

So far, so good. But I have no idea how to get that class *out* of 'AddAccountWindow', so to speak. Either by returning a value... or by passing in an object by reference and turning it into the class that I want.

Creating the class beforehand and using the window to change its attributes is problematic, as a different class is created depending on which account-type is selected.

Any help - or even a pointer towards a similar example - would be greatly appreciated. 

Cheers,

---

