---
title: "Question: C++ GUI  programming for Ubuntu and Windows?"
date: 2010-04-05
forum: Programming Talk
---

### Post by GSMS on 2010-04-05
I have recently finished learning ANSI C++ and I want to move on GUI C++. I was wondering how to make a GUI C++ program that would work on Windows and Ubuntu with the same source.

---

### Post by Some Penguin on 2010-04-05
A search for "cross-platform C++ GUI" would tell you about such toolkits as Qt and wxWidgets.

---

### Post by SledgeHammer_999 on 2010-04-05
And since you learned "Ansi C++" then you have to go with wxWidgets. Qt uses some C++ extensions that make you process your source with their own preprocessor before being able to compile.

---

### Post by MeduZa on 2010-04-05
ubuntu uses GTK+, windows also can, you can use [GTKmm]("http://library.gnome.org/devel/gtkmm-tutorial/unstable/index-info.html.en")
good hacking

---

### Post by Simian Man on 2010-04-05
Either QT or WxWidgets are going to be your best bet.  Using GTK+ on Windows is not a fun experience, believe me.

If you really want your program to look native under any OS, I'd go with wxWidgets because it uses GTK on Linux and the native toolkits on other systems.  Otherwise, QT is the best option because it is very well-designed and has a ton of features.

---

### Post by GSMS on 2010-04-05
> **Simian Man said:**
> Either QT or WxWidgets are going to be your best bet.  Using GTK+ on Windows is not a fun experience, believe me.

If you really want your program to look native under any OS, I'd go with wxWidgets because it uses GTK on Linux and the native toolkits on other systems.  Otherwise, QT is the best option because it is very well-designed and has a ton of features.
Thnaks. :D

---

### Post by weezerBo on 2010-04-05
> **SledgeHammer_999 said:**
> And since you learned "Ansi C++" then you have to go with wxWidgets.
That's bunk. Qt does use the *moc, *but it's all behind the scenes. It doesn't affect the developer at all.

---

### Post by cdekter on 2010-04-05
Personally I would go with QT because I find it much nicer to work with than wxWidgets. That, and QT can now look totally native on Windows, KDE and Gnome (with QGtkStyle).

---

