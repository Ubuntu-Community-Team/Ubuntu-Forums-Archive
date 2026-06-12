---
title: "Python Module for Program Icons"
date: 2009-01-07
forum: Programming Talk
---

### Post by Gannon8 on 2009-01-07
Hello

I am trying to make a program that simply displays a menu of programs with their icon for windows. Is there any library to get both icons in the Windows Registry (Folder Options) and ones attached to exe files?

---

### Post by ankursethi on 2009-01-07
There's this simple module to access the Windows registry - [http://docs.python.org/library/_winreg.html](http://docs.python.org/library/_winreg.html)

Just get a list of installed programs and their corresponding icon paths. In case the icon is embedded in an EXE or DLL, you might need to extract it first. I don't know how to do it, but a bunch of people at StackOverfow seem to know - [http://stackoverflow.com/questions/90775/how-do-you-load-an-embedded-icon-from-an-exe-file-with-pywin32](http://stackoverflow.com/questions/90775/how-do-you-load-an-embedded-icon-from-an-exe-file-with-pywin32)

---

