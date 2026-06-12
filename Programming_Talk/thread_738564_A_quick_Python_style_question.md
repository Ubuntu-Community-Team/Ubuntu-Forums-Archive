---
title: "A quick Python style question"
date: 2008-03-28
forum: Programming Talk
---

### Post by xelapond on 2008-03-28
Hello, 

I'm writing a Python program that has one gigantic string, and many functions that take and process different parts of the string.  So, a quick style question, am I better off having the string global or passing it into each function?

Thanks, 

Alex

---

### Post by LaRoza on 2008-03-28
Perhaps a member of an object?

Do these function belong together?

---

### Post by Can+~ on 2008-03-28
Having global variables is a bad practice, on any language. The best way to implement them on python, is using them inside a class, and use the "self.myvar" to get it.

And wait, are you storing anything on a long string? Like a comma delimited storage or something? because that's one terrible practice.

---

### Post by xelapond on 2008-03-28
There is not reason to implement Object Oriented methods in this project.  I have different function that will parse different parts of a string.  I am writing a really advanced "checkgmail" type thing, its my first "real" program in python.  The file I am parsing is the Gmail Atom feed.

I decided just to pass it through each function, because I have had bad experience with global variables in C on embedded cores.

Ill post the code when I am done.

Thanks, 

Alex

---

