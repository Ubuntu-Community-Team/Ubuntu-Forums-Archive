---
title: "Python: Python23.dll"
date: 2010-09-26
forum: Programming Talk
---

### Post by Sailor5 on 2010-09-26
Ahoy Sailors!

So I'm creating a (hopefully) small application in Python for windows, Now I've compiled it using Py2Exe for Python2.3, Trimmed un-needed modules and compressed the remainder, And finally packed using UPX. All together now it's about nine hundred and something KB's.

I was aiming for anything around eight hundred ideally, The two main culprits are twisted and the main Python dll (Python23.dll), I just wondered is everything inside that file needed? Would it not be possible to recompile it with some things left out?

Failing that does anyone know anything else which mite save some much needed KB's?

Thanks Bye!

---

### Post by lavinog on 2010-09-30
Without knowing any details about your application, it would be tough to offer advice.

The main thing is reduce the number of modules you import.
If you are using the math module for one function, find a way to avoid using that function, or copy the function into your code:
Instead of using sqrt(x) use x**.5

---

### Post by smartbei on 2010-09-30
Don't spend time on removing math - it is built in anyway. (Ditto sys, os, ...).

[This]("http://www.py2exe.org/index.cgi/BetterCompression") looks like an interesting resource... Unless I am missing something, it looks like they got it down to ~800kb. [EDIT: ok, apparently that was for a much simpler project. Might be useful anyway.]

Why do you need to decrease the executable size so much? (less than a single MB is nothing these days)

---

