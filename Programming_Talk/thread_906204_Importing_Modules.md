---
title: "Importing Modules"
date: 2008-08-31
forum: Programming Talk
---

### Post by dodle on 2008-08-31
Can I import a module from a sub-directory?  Say I have my program in directory "a" with a sub-directory "b", can I import a module that is in directory "b"?

---

### Post by Def13b on 2008-08-31
Assuming you mean in Python which judging by your previous few posts is probably the case, there are a few options, personally I use the method listed here,

[Python Docs]("http://docs.python.org/inst/search-path.html#SECTION000410000000000000000")

about path configuration files.

On Ubuntu under /usr/lib/python2.5/site-packages I've added a custom.pth file for the directories I wanted to be able to import from.

---

### Post by dodle on 2008-08-31
Yes, sorry, I was talking about Python.  It seems though, that if i were to do sys.path.append then transferred my applications to another computer it wouldn't be able to import the modules.

---

