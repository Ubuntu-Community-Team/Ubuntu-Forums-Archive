---
title: "Python &quot;Global&quot; Keystrokes?"
date: 2008-03-28
forum: Programming Talk
---

### Post by xelapond on 2008-03-28
I don't really know how to phrase this, but is there a way to have Python recognize keystrokes even if it is not the active application?  I have used PyQt to make Keystrokes do stuff, but these only work when it is the active program.

Thanks, 

Alex

---

### Post by pmasiar on 2008-03-28
I am not sure if I understand, but what is your definition of "active application"? Isn't it the one which will receive user input?

---

### Post by xelapond on 2008-03-28
For instance, if I am currently in Konqueror, and I hit <keystroke> the program, which is not the one currently receiving input, or has window focus, or for that matter, might not even have a GUI, would receive and act upon it(opening a GUI window, for instance)

I hope that helps.  Pretty much If I am in a different application and hit a keystroke it will see it.

---

### Post by scooper on 2008-03-29
Yes, it's possible.  I've done it with python-xlib.  It's not pretty or intuitive either.  I don't have the code handy, but if it would be useful I could try to dig it up.

---

### Post by nanotube on 2008-03-30
see my cross-platform python keylogger project, here:

[http://pykeylogger.sf.net/](http://pykeylogger.sf.net/)

of particular interest to you would be the pyxhook.py file, which uses python-xlib and the X record module to record keystrokes.

like scooper says, it's not pretty - but with the code already in existence, it should be pretty easy for you to just import and use. :)

---

### Post by pmasiar on 2008-03-30
I see, it uses hook deep into X, changing how X handles keystrokes.

I did not know that Python can dive that deep :-) but on other thought, it is just Python binding for that X library, exactly as Python was designed to be used from very beginning. I sometimes forget that not all people use Python for web apps :-)

---

