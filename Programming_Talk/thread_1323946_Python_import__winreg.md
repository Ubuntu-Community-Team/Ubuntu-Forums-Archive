---
title: "Python: import _winreg"
date: 2009-11-12
forum: Programming Talk
---

### Post by jesuisbenjamin on 2009-11-12
Hello there,

in order to install pywin32 module i need the _winreg module (i use python 2.6). _winreg module is not installed, it is part of the python standard library but in spite of searching the net, i cannot find how i am supposed to download and install it.

Any suggestion?

Thanks.

---

### Post by raffaele181188 on 2009-11-12
[http://docs.python.org/library/_winreg.html]("http://docs.python.org/library/_winreg.html")

I think you cannot install it under Ubuntu. It's a Windows-only module

---

### Post by jesuisbenjamin on 2009-11-12
Ah thanks, does this means i cannot install pywin32 either?
I am trying to install win32com and i got the information that i should install pywin32 in which it should be included.

win32com is apparently needed to convert Microsoft Office Documents into text. Which is what i need to do, but under Linux.

Do i have any alternative?

---

### Post by raffaele181188 on 2009-11-12
[On StackOverflow]("http://stackoverflow.com/questions/125222/extracting-text-from-ms-word-files-in-python") there are lots of suggestions ;)

---

### Post by jesuisbenjamin on 2009-11-12
Thanks, i had seen this page already, though i had missed the line that said that pywin32 was for windows only.

All i have found so far to convert doc to txt with python is by calling a subprocess, but this is not what i wish to do because i want my program to be able to convert lots of files temporarily and speedily so it can search through the document with regular expression.

So i guess i will limit my program to docx, which i understand is the format which is now current for Vista and future versions.

---

