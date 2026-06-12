---
title: "GUI Devkits"
date: 2011-08-13
forum: Programming Talk
---

### Post by Grenad on 2011-08-13
I need help deciding on a GUI kit to use for my projects. Now before you tell me that this question has been asked a million times before and that I should just do some research, let me just tell you that I have already researched most of the common options and only need some experienced opinions on each.
 
I need it to be cross-platform, free, usable for open-source and commercial coding, and usable in c, c++, and preferably Python and C# as well. So, Ive pretty much narrowed it down to GTK/GTKmm/GTK#/PyGTK, Qt (LGPL liscense)/PySide, and wxWidgets/wxPython. As far as I know, all of these options meet my criteria. Anyway, if there are any experienced users out there who want to help me out, please drop a post.

---

### Post by cgroza on 2011-08-14
I have experience with wxWidgets and I don't think you can use it with plain C although It has bindings and implementations for many languages and platforms.

I think there is a C# binding because I remember trying to compile it, but never succeeded.

Otherwise, it is a great toolkit, comparable with Qt.

I can't speak for others because I only took tutorials on them and never developed a real program on top of them.

---

### Post by slavik on 2011-08-14
gtk

qt is on it's way since nokia basically killed it.

---

### Post by juancarlospaco on 2011-08-14
HTML5 is my GUI Devkit

---

### Post by Grenad on 2011-08-14
Thanks for the responses!
 
Im still deciding which one im going to start with, but I have a feeling im going to end up learning more than one. As far as im concerned, all of these should be fine as long as I can use them for commercial products WITHOUT having to pay for the kit or paying royalties for commercial use (ehem...Qt). I know that I can use GTK for commercial, closed source use as long as I dynamically link with the library and dont modify the GTK source code. Im not sure about wxWidgets and Qt though. I think wxWidgets iscense is essentially LGPL with some modifications, and I think Qt has an LGPL liscense now that I can use as long as i comply with the LGPL. (Please verify).
 
Anyway, my main problem right now is native look and feel since all of these are obviously good options for me. As long as the kit is compatible with c++ and python im happy. So, which of these would be good for cross-platform development? I know that wxWidgets tries to use some native objects when possible, but I dont know how far this will go to make the program actually FEEL native rather then just little hints here and there. Qt and GTK look practically the same across different platforms, but GTK is mainly for GNU Linux (so ive heard). Any suggestions?

---

### Post by terry_a_g on 2011-08-14
> **slavik said:**
> qt is on it's way since nokia basically killed it.
Perhaps you can back that up with some facts?  Worst case scenario Nokia stops developing QT and it ends up on equal ground with GTK as a community developed toolkit. Staff spreading FUD is wrong.

---

### Post by slavik on 2011-08-15
> **terry_a_g said:**
> Perhaps you can back that up with some facts?  Worst case scenario Nokia stops developing QT and it ends up on equal ground with GTK as a community developed toolkit. Staff spreading FUD is wrong.
Nokia is dropping Meego which is the whole reason it bough QT to begin with. I do not see a reason for Nokia to develop QT further.

I am not staff. :(
EDIT: Looks like being a mod does make me staff. Well, do not take as anything that Canonical would say. My opinion, so on so forth. Standard legal disclaimer.

---

### Post by GeneralZod on 2011-08-15
I wouldn't worry too much about the future of Qt; it's pretty uncommon for a company to start working on the next major revision of a piece of software they intend to drop soon :) And as mentioned, in the worst case Qt ends up being roughly level with Gtk & WxWidgets in terms of paid developers, and has a lot of invested parties in industry.

Incidentally: I note with interest that long-time Trolltech (and then Nokia) employee Thiago Maceira has left to join Intel's open source division.  Intel are, of course, the other major player in the Qt-based Meego project.  I would not be even slightly surprised to see them adopt Qt (or at least, a large chunk of the current employes) should the worst come to the worst.

---

### Post by juancarlospaco on 2011-08-15
:p

---

### Post by slavik on 2011-08-16
> **GeneralZod said:**
> I wouldn't worry too much about the future of Qt; it's pretty uncommon for a company to start working on the next major revision of a piece of software they intend to drop soon :) And as mentioned, in the worst case Qt ends up being roughly level with Gtk & WxWidgets in terms of paid developers, and has a lot of invested parties in industry.

Incidentally: I note with interest that long-time Trolltech (and then Nokia) employee Thiago Maceira has left to join Intel's open source division.  Intel are, of course, the other major player in the Qt-based Meego project.  I would not be even slightly surprised to see them adopt Qt (or at least, a large chunk of the current employes) should the worst come to the worst.
That makes sense, but it would still be uneasy to develop with QT. There is still uncertainty there.

---

### Post by llanitedave on 2011-08-16
I'm using WxPython, but I would definitely hate to see QT get orphaned.  I too think it's more likely that some other organization, whether commercial or community, will pick it up. I don't think it's likely to be suppressed.

And yes, to the OP, I find the WxPython version of WxWidgets, at least, to be quite easy (if you can call any GUI "easy"!) and even enjoyable to work with.

---

### Post by Grenad on 2011-08-17
I agree python is an excellent language for GUI development. However, it is not good for closed-source development since it is an interpreted language. That is why I need the GUIkit to be compatible with another language, preferably c++.

---

### Post by slavik on 2011-08-17
QT is written in C++ so it's native there.
GTK has C++ wrappers to make it more C++ called gtkmm.

Those are the two gorillas on the Linux desktop.

---

### Post by Grenad on 2011-08-17
Thanks slavik. I am going to be developing on windows since arch linux killed my old computer (dont ask how) and I dont want to mess with my new lappy. But I certainly hope to make my programs cross-platform for linux. Thats why I want a cross-platform GUI kit. By the way things are right now, I am probably going to go with gtk or qt, but im going to wait until im done with my current windows project (ugh) to decide.
 
One more question. Do these kits come in dll form? Because if they dont, its going to be a pain in the butt to dynamically link to them in order to comply with the LGPL for closed source products (correct me if im wrong. this is what i concluded after a couple minutes of google).

---

### Post by slavik on 2011-08-17
I don't know about QT, but gtk has an installable package for windows. Pidgin for windows comes with it. I am pretty sure QT has a similar thing.

---

### Post by Grenad on 2011-08-17
Yes, QT has an installer package for windows, and it comes with some goodies too. And GIMP also comes with a version of GTK.

---

### Post by slavik on 2011-08-18
Gathered the links. :)

QT: [http://qt.nokia.com/downloads/downloads#qt-lib](http://qt.nokia.com/downloads/downloads#qt-lib)
GTK: [http://www.gtk.org/download/index.php](http://www.gtk.org/download/index.php)

---

### Post by GeneralZod on 2011-08-18
If you go for Qt under Windows, you might want to download the full SDK - it's a bit of a monster, but since it comes bundled with (the very slick) QtCreator, you'll be able to be productive straight away.

---

### Post by juancarlospaco on 2011-08-18
HTML5, download nothing, run everywhere: [http://arcade.rawrbitrary.com/mario/](http://arcade.rawrbitrary.com/mario/)

---

