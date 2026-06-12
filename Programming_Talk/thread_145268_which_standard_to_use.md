---
title: "which standard to use?"
date: 2006-03-15
forum: Programming Talk
---

### Post by uten on 2006-03-15
I am doing a project for OOP its written in C++. some guys decided to step it up a notch and used gui for their project and everyone is oohh and ahhh, and really it is quite easy to do in windows but anyway im digressing.

I decided i would also do gui, but in my open source ways it has to be able to run on mac/win/lin with little code modification.

ive done my research and i can use gtk or wxwidgets or qt.

have any of you guys used these? which would you suggest?

so far i am leaning towards wxwidgets. GTK is based on C so its not quite suitable. I have found how-tos for porting windows wx code to linux but this is quite the other way around. Natively I will be writing this to work on my kubuntu laptop and porting it to windows.

here are some nice reads for thos einterested:
[http://www.codeproject.com/library/wxwidgets.asp](http://www.codeproject.com/library/wxwidgets.asp)
[http://www.novell.com/coolsolutions/feature/11244.html](http://www.novell.com/coolsolutions/feature/11244.html)

---

### Post by celloandy on 2006-03-16
I'm not much of a C++ coder, but just for reference, Gtk+ has good C++ bindings, and they're used in major projects like Inkscape.  Take a look at [http://www.gtkmm.org/](http://www.gtkmm.org/) for more info.

As for what you should use, I'd say it depends on your target platform.  wxWidgets works the best on Windows, but doesn't look very natural over Gnome, despite the fact that it uses Gtk+, because the stock icons and everything don't match.  Gtk+ looks the best under Gnome and will also run under Windows, and I've heard good things about the above-mentioned gtkmm, though I've never used it.  Qt will look good under KDE, but won't run under Windows without a license from Trolltech.

Andrew

---

### Post by Single on 2006-03-16
[QUOTE=celloandy]Qt will look good under KDE, but won't run under Windows without a license from Trolltech.[/QUOTE]

Qt opensource edition runs on Windows, Mac, and Linux since version 4.
For crossplatform toolkit, Wxwidget and Qt are suitable. But Qt's api is much cleaner.

---

### Post by uten on 2006-03-16
[QUOTE=Single]Qt opensource edition runs on Windows, Mac, and Linux since version 4.
For crossplatform toolkit, Wxwidget and Qt are suitable. But Qt's api is much cleaner.[/QUOTE]

i went to their open source download page, it doesn't allow me to download a version for windows. so after i code my qt in kdevelop how do i compile it for windows? i know with wxwidgets i could compile it in the free microsoft compiler thingy, i 4get the name. Trolltech has an educational option to get a qt license for windows but its only for lecturers who want to teach qt.

i would really like to code for qt but i may have to settle with wx widgets

ps. i prefer coding for kde because thats what my friends and i mostly use

---

### Post by uten on 2006-03-16
whoops, found the download page for qt windows. I'm still open for suggestion though

---

### Post by hod139 on 2006-03-16
The only other cross-platform c++ windowing toolkit that I know of is [fox]("http://www.fox-toolkit.org/").  I would suggest either fox or wxWidgets.

---

### Post by uten on 2006-03-19
ok well i am using qt, except when using kdevelop to make an application it doesn't run by default, ive added all the qt4 stuff from repositories, is there something else i need?

---

### Post by wyo on 2006-04-06
[QUOTE=uten]
I decided i would also do gui, but in my open source ways it has to be able to run on mac/win/lin with little code modification.
[/QUOTE]

If you need to support Linux/Mac/Windows there is IMO no alternative to wxWidgets ([http://www.wxwidgets.org](http://www.wxwidgets.org)). wxWidgets is the only one who looks native on all 3 platform, GTK+ is just a C framework and OpenSource QT-Code is almost none existent outside of KDE. Fox, FLTK, etc don't have the necessary resource to compete against the big three albeit they might be quite useful under special circumstances. But if you want a full featured framework suitable for each platform you're best off with wxWidgets.

If you just started a new project you should look into wyoGuide ([http://wyoguide.sf.net](http://wyoguide.sf.net)) which has a full featured base application well suited as the starting base code of your project. Menu, statusbar, help, i18n, etc. code is already there, only your project specific code is missing. And this way your app will run just from the beginning.

O. Wyss

---

### Post by uten on 2006-04-06
ok thanks, will check it out

---

