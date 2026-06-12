---
title: "BlueFish File Format"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Nutopia on 2008-07-23
Hi,

I'm using Bluefish and everything is ok with me, except a co-worker who is on a Windows machine sees my files as 'scrambled' until he changes the File Format from Windows to Unix. Does anyone know of a setting that could be screwy?

Thanks!

---

### Post by LowSky on 2008-07-23
I'm kinda confused by what your asking because Bluefish isn't supported in Windows. It was designed using POSIX compatible operating systems including Linux, FreeBSD, Mac OS-X, OpenBSD, Solaris and Tru64.

So what program is your co-worker using to view the files?

---

### Post by Nutopia on 2008-07-23
My coworker is using EditPlus 3

---

### Post by LowSky on 2008-07-23
ok another thing I should have asked before. What format are you writing code in? Java, Html, C, something else...? How is he recieving the file from you, your local hard drive, email, shared network storage? what do you mean scrabmled? How is he changing the file format from linux to windows, That doesn't make sense to me as the extentions should be the same.

---

### Post by LowSky on 2008-07-23
here is a list of editor that work across platforms
[http://en.wikipedia.org/wiki/Comparison_of_text_editors#Cross-platform](http://en.wikipedia.org/wiki/Comparison_of_text_editors#Cross-platform)

---

### Post by Nutopia on 2008-07-23
It appears like the line ending character is not correct. He said that the code looks like it's all written on top of each other. He receives the files using SVN - I'm using RapidSVN and he uses Tortoise. To fix the files here is what he does:

> 
[LIST]
[*]in my editor - Document->File Format (CR/LF)->Change File Format ...
[*]when the dialog box comes up
[*]I change from PC to UNIX
[*]and hit OK, then save the file
[*]then I do Document->Reload
[/LIST]


The code is mostly PHP

---

