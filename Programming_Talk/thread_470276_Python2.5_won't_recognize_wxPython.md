---
title: "Python2.5 won't recognize wxPython"
date: 2007-06-10
forum: Programming Talk
---

### Post by Occasionally Correct on 2007-06-10
Hey guys, first time that I've posted here, but I've lurked for answers before. :)

I tried to find an answer to my current problem but came up short. For some reason, Python 2.5 isn't recognizing that I have installed wxPython 2.8. After a lot of uninstalling and reinstalling, I ran Python 2.4 from the terminal and found out that wxPython is actually working there. When I try to import the wx module in python2.5 however, it says that it wasn't found.

I've been looking around for a way to "redirect" it so that it works with 2.5, but I haven't been able to figure anything out.

All help is appreciated. I'm running on Feisty if that's any help too. :)

---

### Post by 5-HT on 2007-06-10
Hi,

Do you have your PATHs set up correctly for: wxpython's bin, LD_LIBRARY_PATH, & PYTHONPATH?
[http://www.wxpython.org/builddoc.ph]("http://www.wxpython.org/builddoc.php")

---

### Post by Occasionally Correct on 2007-06-10
I had played around with the path, but nothing was working. Eventually I got what I needed from ubuntu package search in firefox. It turns out that the python-wxgtk2.8 package in the repos was only installing it for python2.4 (the one I just got installed for python2.5).

So everything works now. Thanks for the response! :)

---

