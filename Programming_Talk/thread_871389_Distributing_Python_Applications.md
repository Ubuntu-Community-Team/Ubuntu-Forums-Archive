---
title: "Distributing Python Applications"
date: 2008-07-26
forum: Programming Talk
---

### Post by kidko on 2008-07-26
I'm currently developing a cross-platform (Windows and Linux are the two target systems) WxPython application. My question: without access to a Windows machine, is there a good way to distribute this app without requiring the user to install Python and WxPython libraries? I know Chandler ([http://chandlerproject.org/](http://chandlerproject.org/)) does it, but I haven't been able to dig up anything.

---

### Post by nanotube on 2008-07-27
> **kidko said:**
> I'm currently developing a cross-platform (Windows and Linux are the two target systems) WxPython application. My question: without access to a Windows machine, is there a good way to distribute this app without requiring the user to install Python and WxPython libraries? I know Chandler ([http://chandlerproject.org/](http://chandlerproject.org/)) does it, but I haven't been able to dig up anything.

well, there is py2exe, but that requires a windows install to build on...

why don't you ask the chandler guys how they do it? (and post back here, as i'm curious :) ).

---

### Post by tamoneya on 2008-07-27
shouldnt py2exe work under wine?

---

### Post by LaRoza on 2008-07-27
> **kidko said:**
> I'm currently developing a cross-platform (Windows and Linux are the two target systems) WxPython application. My question: without access to a Windows machine, is there a good way to distribute this app without requiring the user to install Python and WxPython libraries? I know Chandler ([http://chandlerproject.org/](http://chandlerproject.org/)) does it, but I haven't been able to dig up anything.

Chandler probably just includes the interpreter and libraries as part of the install program.

Installing Python (recommend ActivePython) and wxPython is easy, simple installers.

---

### Post by nanotube on 2008-07-27
> **tamoneya said:**
> shouldnt py2exe work under wine?

possibly - but it appears to be a major pain to get it to work, and includes downloading windows dlls:
[http://mail.python.org/pipermail/python-list/2004-July/269445.html](http://mail.python.org/pipermail/python-list/2004-July/269445.html)

---

### Post by kidko on 2008-07-27
Well, ActivePython and the WxPython installers seem to be the easiest thing at this point, but I've also shot off an email to the Chandler technical crew, asking how they managed it. If they write back, I'll let you guys know.

---

### Post by samjh on 2008-07-28
One way you can do it is by creating a self-contained Python installation yourself.  Grab a copy of Python for Windows, install it, and trim out any libraries or files you don't need from the C:\Python25 directory.  Then make a customised launcher (you can make a simple C program in Linux and compile using mingw32) to be the file that your users double-click on to run your program.

---

### Post by themusicwave on 2008-07-28
I recently had the same problem at work.  I needed to distribute a Python Application on Windows.

What I ended up doing was writing my own installer(in Python) to install the application.

The first thing I had my installer do was install Python 2.5 and set their path.  Then I was able to simple run the ordinary Python code just fine.


I used py2exe to create the installer and bundled an MSI of Python 2.5.  The installer then installs Python and the application together so it all works seamlessly.  The Python install is silent too, so the user doesn't even have to know/care.

Now all the servers I have int the field have Python on them and I can use it to script for them.  Let me tell you it sure beats using VBScript or having to write a custom C# exe every time I need to do maintenance work on them.

---

### Post by nvteighen on 2008-07-28
> **themusicwave said:**
> 
I used py2exe to create the installer and bundled an MSI of Python 2.5.  The installer then installs Python and the application together so it all works seamlessly.  The Python install is silent too, so the user doesn't even have to know/care.

Which reminds of something that happened to me yesterday in a Windows box: an application ended up firing a Tcl interpreter I didn't know about! Not too silent...

---

