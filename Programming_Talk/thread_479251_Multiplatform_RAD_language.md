---
title: "Multiplatform RAD language"
date: 2007-06-20
forum: Programming Talk
---

### Post by Primus on 2007-06-20
Linux and Ubuntu Noob here. :D

Can anyone make any suggestions as to a good RAD development system that would allow me to build forms and reports for a MySQL back end database?

It would be really cool if it could create code that would run on Windows too. Maybe I am asking too much but any suggestions as to a good, robust RAD development language would be most appreciated.

I currently use MS Access for a lot of RAD work - yes I know Access has lots of problems (such as being single file and slow in busy environments) but it is an excellent RAD tool. More importantly - for me at least - it is the single remaining reason why I cannot move completely away from Windows.

I don't want to start lots of flames against Access - I know them all ;) - but suggestions as to Ubuntu alternatives would be most helpful. Thanks. :)

---

### Post by pmasiar on 2007-06-20
is it web application I assume? Python and TurboGears. Cross-platform no problem.

---

### Post by Primus on 2007-06-20
I was actually thinking more along the traditional lines of a client - server application without running in a web browser. However - I will take a look at TurboGears - I hadn't heard of that one before.

I am just looking to replace my current RAD development environment (MS Access) with something that is more robust and can preferably compile to both Windows and Ubuntu.

---

### Post by pmasiar on 2007-06-20
with AJAX, web-based app is "almost" as responsible as traditional desktop.

Of course user need to be online, and javascript is harded to debug etc (but cross-browser libraries are emerging to solve incompatibilities)  - but also you have only 1 place to deploy, upgrading and version synchronization is non-problems.

Not mentioning that with AJAX, you are fully buzzword-compliant as a bonus :-)

---

### Post by kknd on 2007-06-20
Python is a good RAD language.
If you want to do only some database acess, you can use the OpenOffice Base

---

### Post by pmasiar on 2007-06-20
SQLite is simplest SQL DB I know of, and is included in Py2.5 (and very simple to install for Py2.4)

---

### Post by Primus on 2007-06-20
> **pmasiar said:**
> with AJAX, web-based app is "almost" as responsible as traditional desktop.

Not mentioning that with AJAX, you are fully buzzword-compliant as a bonus :-)

:D Thanks for your suggestions!

---

### Post by Primus on 2007-06-20
> **kknd said:**
> Python is a good RAD language.
If you want to do only some database acess, you can use the OpenOffice Base

I see. So is there a native forms editor for Python or do I look to programs such as Base for this?

---

### Post by pmasiar on 2007-06-20
If you do web front-end for a database - HTML is your forms, and any HTML-capable editor will do: but skip notepad and start with SciTE or better editor.

I don't do desktop GUI so i cannot tell from my own experience, but people say that Glade and wxPython is the way to go - you may double-check that with experts, I have no idea what API and services Base includes.

---

### Post by Smygis on 2007-06-20
> **Primus said:**
> I see. So is there a native forms editor for Python or do I look to programs such as Base for this?

"forms editor"... Is that microsoftish for GUI designer? Ive heard the words a lot around the .net camp. But what it is is beyond me.

wxGlade is a good GUI designer for wxWidgets. 

And look on the 20 Minute Wiki screencast from turbogears. Man, For me web development is to much magic. But Turbogears is darn impressive.

[http://files.turbogears.org/video/20MinuteWiki2nd.mov](http://files.turbogears.org/video/20MinuteWiki2nd.mov)

---

### Post by Primus on 2007-06-20
> **Smygis said:**
> "forms editor"... Is that microsoftish for GUI designer? Ive heard the words a lot around the .net camp. But what it is is beyond me.


Yes. A GUI designer. In the MS world the screens for all business apps tend to be called forms. I'll take a look at your suggestions. Thanks! :)

---

### Post by kknd on 2007-06-21
You can use Glade, a visual UI designer (you can call it form designer if you want) withe the GTK+ bindings for Python (PyGTK).

---

### Post by ByteJuggler on 2009-03-10
[Lazarus]("http://www.lazarus.freepascal.org/") is worth a look, and cross platform too.

---

