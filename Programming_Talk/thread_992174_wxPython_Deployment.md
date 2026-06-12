---
title: "wxPython Deployment"
date: 2008-11-24
forum: Programming Talk
---

### Post by themusicwave on 2008-11-24
So I am thinking of converting some TKinter apps over to wxPython because it looks much nicer.

However, the major drawback is that wxPython isn't included with Python by default.  How do I go about deploying it in a seamless way.  I know I could just give them the wxPython installer, but I would like it to be an invisible process.

I can't find much information on the topic anywhere.  Any ideas?

---

### Post by Majorix on 2008-11-24
For deploying for Windows you can use [py2exe]("http://www.py2exe.org/") which runs on Windows and compiles .py to .exe, along with the necessary/used libraries. I don't know if such a tool exists for deploying Linux apps.

EDIT: Sorry, I forgot about FreezePython, which does about the same job, but for Linux. Might want to look into it.

---

### Post by themusicwave on 2008-11-24
I am familiar with py2exe and have considered it.  I am hoping to keep the program as a .py file.  I need to be able to e-mail it to technicians.  Our firewalls forbid .exe e-mails, which is part of the benefit of Python.  Our firewalls and most other firewalls let .py files through.

I can have them install wxPython and Python, I was just hoping to avoid that and keep it somewhat clean.

---

