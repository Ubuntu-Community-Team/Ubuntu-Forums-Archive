---
title: "[SOLVED] A trivial database?"
date: 2008-04-26
forum: Programming Talk
---

### Post by WitchCraft on 2008-04-26
Hi! Question:

I want to use a tiny database with C++, but I don't want the user to install MySQL or any such thing. 

Isn't there something, like GNU database? I think I once saw it, but I don't remember the name... 

I think it's some kind of trivial-database library to include with your program...

---

### Post by Can+~ on 2008-04-26
> **WitchCraft said:**
> Hi! Question:

I want to use a tiny database with C++, but I don't want the user to install MySQL or any such thing. 

Isn't there something, like GNU database? I think I once saw it, but I don't remember the name... 

I think it's some kind of trivial-database library to include with your program...

[SQLite](http://en.wikipedia.org/wiki/SQLite). edit: Wikipedia says sqlite has bindings with C++.

---

### Post by pmasiar on 2008-04-26
BDM is even simpler - has no SQL, just key-value.

---

### Post by nhandler on 2008-04-26
Another simple option is to store all of the data in a text file. You wouldn't need any additional programs installed, it isn't too hard to implement in the code, and it is easy to manually modify the file. You might even consider using a .csv (comma separated values) file as the db. That way, you could use a spreadsheet application to create/edit the db.

---

### Post by LaRoza on 2008-04-26
> **WitchCraft said:**
> I want to use a tiny database with C++, but I don't want the user to install MySQL or any such thing. 


All of the suggestions here will work, but what exactly are you storing?

---

### Post by WitchCraft on 2008-06-21
> **LaRoza said:**
> All of the suggestions here will work, but what exactly are you storing?

Redundance :lolflag:

---

