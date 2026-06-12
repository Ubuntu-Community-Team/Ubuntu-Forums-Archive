---
title: "The best way to program for KDE and GNOME at the same time, so the app works on both)"
date: 2007-01-02
forum: Programming Talk
---

### Post by systemintheglitch on 2007-01-02
I want to make a program that will work for both desktop environments, but if the user has gnome, it will use the gnome widgets/windowbar and if the user has kde it will use the kde widgets/windowbar etc.

---

### Post by cime on 2007-01-02
Maybe java + swing?

---

### Post by coder_ on 2007-01-02
Won't wxWidgets do that?  Forgive me if I'm wrong, maybe it's just cross platform, not cross-toolkit.

---

### Post by -Rick- on 2007-01-02
Maybe you could create a GTK+ and a Qt frontend and let the user run a (ba)sh script which decides which to use.
Also I remember vaguely that Qt 4 has some GTK support.

---

### Post by Mirrorball on 2007-01-02
I don't see any problem about running a GTK app on KDE or a Qt app on Gnome. With Qt-GTK (or is it GTK-Qt?) they even look the same. Just don't use any specific Gnome or Qt library, although this is not really a problem either.

---

### Post by Houman on 2007-01-02
Hi

wxwidgets is a very good option, as coder_ mentioned (and yes it runs in both gtk, and qt and anythign else as long as the proper runtime libraries are installed).

Also teh benefit of using wxwidgets is that you can also use it in windows and other OSes as well

regards

Houman

---

### Post by Mirrorball on 2007-01-02
Qt and GTK run on Windows too. Not sure on Mac.

---

### Post by kalikiana on 2007-01-02
Personally I have the impression that wxWidget apps are only partly looking like e.g. Gtk+2 apps, for example I believe there is no icon theme support. Please correct me if I'm wrong.

---

### Post by Houman on 2007-01-02
```
Qt and GTK run on Windows too. Not sure on Mac.
```

Yes but gtk support on windows leaves a lot to be desired (it sucks). And QT has the whole problem with their restrictive license (you gotta pay trolltech in certain scenarios, like if you are commercially developing, which is reasonable i think).

wxWidgets is completely free and designed with crossplatformability (i made up that word) in mind, as opposed to the windows port of gtk which came as an afterthought. 

As for the icon theme support I dont really know :(

regards

---

