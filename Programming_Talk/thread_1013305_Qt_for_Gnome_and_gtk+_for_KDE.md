---
title: "Qt for Gnome and gtk+ for KDE?"
date: 2008-12-16
forum: Programming Talk
---

### Post by kcode on 2008-12-16
Is the above combination wrong? Is developing application in Qt for Gnome desktop environment and in gtk+ for KDE a wrong thing to do? If yes, how does it really effect?

Thanks

---

### Post by OutOfReach on 2008-12-16
Of course not, there's nothing wrong with that kind of development. The only real 'bad effect' would be the theme/native look. That's why people say that mixing the two (qt + Gnome, Gtk + KDE) is a bad thing.

---

### Post by jimi_hendrix on 2008-12-16
then whats the advantage of using Qt and GTK+?

---

### Post by kcode on 2008-12-16
> **OutOfReach said:**
> The only real 'bad effect' would be the theme/native look.


What doew it mean?

---

### Post by ZuLuuuuuu on 2008-12-16
> **kcode said:**
> What doew it mean?

It means GTK applications does not look good in KDE and Qt applications does not look good in Gnome :)

---

### Post by bruce89 on 2008-12-16
> **jimi_hendrix said:**
> then whats the advantage of using Qt and GTK+?

GTK+ is under the LGPL, Qt (FOSS edition) under the GPL. Commercial software can use GTK+ for no cost, Qt if they buy a licence.

---

### Post by samjh on 2008-12-17
> **kcode said:**
> Is the above combination wrong? Is developing application in Qt for Gnome desktop environment and in gtk+ for KDE a wrong thing to do? If yes, how does it really effect?
No it's not wrong at all.

GTK+ applications work well in KDE and Qt applications work well in Gnome.  Even look-and-feel is emulated for each platform.  GTK+ applications use a Qt theme engine when running in KDE, and Qt applications have a GTK+ engine for running under Gnome.

> **jimi_hendrix said:**
> then whats the advantage of using Qt and GTK+?

Qt: a library which incorporates GUI, networking, threading, security, graphics, databases, and other functions in an intuitive, well-documented and widely supported library.  It is also FOSS under the GPL license.

GTK+: a light-weight and popular GUI library with a very liberal license, the LGPL.

Both are multi-platform, free and open-source (although Qt requires commercial license for closed-source projects), popular, and proven to be effective at what they are designed to do.

If you like programming in C, or target the Gnome environment, then GTK+ is good.  If you like programming in C++, or target the KDE environment, or want a library that does "everything", then Qt is good.  Both have bindings for multiple programming languages aside from their primary language: Ada, Python, Ruby, etc.

---

### Post by ZuLuuuuuu on 2008-12-17
> **samjh said:**
> 
Qt: a library which incorporates GUI, networking, threading, security, graphics, databases, and other functions in an intuitive, well-documented and widely supported library.

GTK+: a light-weight and popular GUI library with a very liberal license, the LGPL.

If you like programming in C++, or target the KDE environment, or want a library that does "everything"

Actually GTK also has a lot of functionality along with graphical toolkit; like threading, string manipulation (XML parsing, regular expressions), timers etc. But it is a fact that Qt is more comprehensive and I guess its Mac port is more complete.

---

### Post by nvteighen on 2008-12-17
> **jimi_hendrix said:**
> then whats the advantage of using Qt and GTK+?
Well, first of all, if you're coding in C, you can't use Qt because there are no bindings.

I actually don't see major differences and the choice may actually be more related to what platform you're targeting and, at last, at your preferences. None of both has a technical superiority on the GUI toolkit and both do their jobs well.

Qt also offers some non-GUI stuff... GTK+ offered some too before but are now part of GLib.

---

### Post by mssever on 2008-12-17
> **samjh said:**
> GTK+ applications work well in KDE and Qt applications work well in Gnome.  Even look-and-feel is emulated for each platform.  GTK+ applications use a Qt theme engine when running in KDE, and Qt applications have a GTK+ engine for running under Gnome.
Not necessarily. I'm not a KDE user, so I can't speak to GTK apps in KDE. But I do know that the only way to make Qt apps match the GTK theme is to install separate software, which isn't installed by default.

Furthermore, there's a difference between following a theme and matching L&F. Qt and GTK differ, for example, in icon usage, dialog design (such as about dialogs and save dialogs), and such things. Additionally, GNOME and KDE follow different style guides. So for example, GTK apps should generally follow Gnome convention and make most dialogs auto-applying. KDE is more traditional in that way, so Qt should normally follow that style.

---

### Post by OutOfReach on 2008-12-17
> **samjh said:**
> 
GTK+ applications work well in KDE and Qt applications work well in Gnome.  Even look-and-feel is emulated for each platform.  GTK+ applications use a Qt theme engine when running in KDE, and Qt applications have a GTK+ engine for running under Gnome.


Not by default. Native look is not emulated by default. Qt has QGtkStyle (third-party) works pretty well but really doesn't do it perfectly. The closest thing GTK has to a native look on a Qt enviroment is QtCurve (third-party, which only emulates colors, not widget styles), and GTK-Qt (again, third-party) an engine that emulates widgets and colors, but nowhere close to perfect.

---

### Post by samjh on 2008-12-17
QGtkStyle will come with Qt 4.5.

In Qt 4.2 to 4.4, there is Cleanlooks available under Qt Config (which is installed by default) which is an imitation of Clearlooks.  Not perfect, but pretty close.

GTK under KDE looks pretty darned ugly until you install third party themes for them.  It's not an issue for Kubuntu as it's installed by default, but it becomes an issue if you want to customise the installation and forget to include the right packages.

> **ZuLuuuuuu said:**
> Actually GTK also has a lot of functionality along with graphical toolkit; like threading, string manipulation (XML parsing, regular expressions), timers etc. But it is a fact that Qt is more comprehensive and I guess its Mac port is more complete.

You're talking about GLib, right?  That's a dependency of GTK+, but still a separate library.

---

### Post by snova on 2008-12-17
Ah, I wanted to mention.

Technically, you don't use Qt under KDE, you use KDE. :P

---

### Post by OutOfReach on 2008-12-17
> **samjh said:**
> QGtkStyle will come with Qt 4.5.

Hmm. Was not aware of this, nice.


But anyways, yes GTK apps in a Qt enviroment do look very unpleasant.

---

### Post by kcode on 2008-12-17
Thanks all.

Another thing, does integration of an application with the desktop environment will an issue, if the application is developed not using the native library in which the desktop environment is written?

Check out this thread, [http://ubuntuforums.org/showthread.php?t=1014134](http://ubuntuforums.org/showthread.php?t=1014134)

Thanks

---

### Post by bruce89 on 2008-12-17
> **snova said:**
> Technically, you don't use Qt under KDE, you use KDE. :P

That's interesting, as these days you don't use GNOME libraries any more. Essentially, there is no need to use GNOME libraries as they have mostly been replaced with things in GLib (GIO) and GTK+ itself.

---

### Post by mssever on 2008-12-17
> **kcode said:**
> Thanks all.

Another thing, does integration of an application with the desktop environment will an issue, if the application is developed not using the native library in which the desktop environment is written?

Check out this thread, [http://ubuntuforums.org/showthread.php?t=1014134](http://ubuntuforums.org/showthread.php?t=1014134)

Thanks
It will work in all environments. However, in a non-native environment it will probably look out-of place, and pulling in additional dependencies could be a problem. For example, in a default Ubuntu install, Qt and KDE are not installed. So if you want to install a Qt app, you also have to download and install the Qt dependencies. If the app also uses KDE stuff, you could wind up with half of KDE as dependencies just to install a single app. And trying to mix Qt and GTK/GLib in a single app is the path to insanity.

If you're using Qt, do stuff in a KDE style. If you're using GTK, do stuff like Gnome or Xfce.

---

### Post by Envergure on 2009-01-22
I have used Qt in programs written on GNOME.  It runs fine, no problem.

---

