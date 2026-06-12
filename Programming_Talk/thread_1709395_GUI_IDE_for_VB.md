---
title: "GUI IDE for VB"
date: 2011-03-18
forum: Programming Talk
---

### Post by THE_An0mOLy! on 2011-03-18
Okay so,

Basically I'm looking for an IDE with a GUI designer for VB in Ubuntu 10.10. Yes I know VB is a sucky language etc, but I've had to learn it for my course and don't have the time to learn a new :D
 
Basically I just need a program which will allow me to code+compile + design a gui (with buttons/widgets/forms/windows/whatever) in visual basic.

I've look around at monodevelop which doesn't have a gui for vb and I've read plenty about using GtK# to do so... but I don't want to have to learn a new language... or have to design my own gui editor or something?

Any help would be GREATLY appreciated. :)

---

### Post by dv3500ea on 2011-03-18
Try [gambas]("http://gambas.sourceforge.net/en/main.html") [[IMG]http://bit.ly/software-small[/IMG]]("http://apt.ubuntu.com/p/gambas2").

> 
Gambas is a free development environment based on a Basic interpreter with object extensions, a bit like Visual Basic&#8482; (but it is NOT a clone !). Read the [introduction]("http://gambas.sourceforge.net/en/main.html") for more information. 

With Gambas, you can quickly design your program GUI with QT or GTK+, access MySQL, PostgreSQL, Firebird, ODBC and SQLite databases, pilot KDE applications with DCOP, translate your program into any language, create network applications easily, make 3D OpenGL applications, make CGI web applications, and so on...


---

### Post by andrew1992 on 2011-03-18
Is there any reason that you must do this on Ubuntu? I understand that you're doing this for a school assignment, so is there any way you can get access to a Windows machine? .NET and Visual Studio I would think is the way to go with VB.

---

### Post by raydeen on 2011-03-18
You could try running VB in WINE. It looks like VB6 (fairly old) has gold status and VB Express 2008 has bronze status.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=94](http://appdb.winehq.org/objectManager.php?sClass=application&iId=94)

I would second the recommendation for Gambas if you don't need your apps to run on a Windows box. It seems similar enough that you wouldn't have to relearn too much, maybe just slightly different keywords or functions.

---

### Post by rg4w on 2011-03-18
You might consider REALBasic.  It's a proprietary commercial product, but if that's not a show-stopper for you it has a pretty good reputation and runs on Linux, Windows, and OS X.

I haven't used it myself in many years (I use a similar multi-platform tool with a very different language called LiveCode), but I have many friends who do and they speak quite highly of it for rapid development of GUI apps.

---

### Post by forrestcupp on 2011-03-18
If you need real VB, you need to be using Windows. MonoDevelop is the best we have, and it's GUI creator is only for C#.

---

### Post by THE_An0mOLy! on 2011-03-19
Thanks for all your suggestions guys :)

Unfortunately I'm limited to VB so they examiners can mark it and the reason it needs to be ubuntu is because I installed it on my laptop so it's actually usable :D As opposed to full-fat vista which took ten minutes to open word >_>

I do have access to visual studio in school but only via a virtual machine - one in which you cannot save and hence have to transfer things across to the main account every time you need to save >_> AND you can only transfer certain files/info - namely copypasta text and for some reason zip files -.-

But I can't believe I didn't think of trying wine with the actual visual studio, Thank you! :D

*rushes off to find laptop*

---

