---
title: "question about interfaces and code portability (gnome, kde)"
date: 2010-04-24
forum: Programming Talk
---

### Post by Søren on 2010-04-24
im just getting ready to have a go at building some interfaces on ubuntu/using gnome. ive worked out that gtk and qt are the two most portable toolkits for this. what im wondering has to do with the api involved in making gui's on a gnome system. if i use qt, say, will the code only work on systems that have qt installed? i really want to keep it as simple as possible and portable too. what is the most portable api i can use of linux? is there and way you can write code that works for kde and gnome?

---

### Post by nvteighen on 2010-04-24
GTK+ programs can run under KDE and Qt ones can run under GNOME perfectly (maybe just looking a bit awkward without further configuration) if the libraries are installed. The libraries won't conflict or anything, but yes, you have to have them installed if you want the program to work.

But there's something called wxWidgets that grabs the native GUI toolkit and uses it without you having to change your code. It even works on Windows. Maybe that's the most portable solution of all, but again the wxWidgets libraries have to be installed to make this work... the other alternative I can think of is to create .debs that mark the needed libraries as dependencies.

---

### Post by Lux Perpetua on 2010-04-24
The most portable toolkit for building interfaces is probably ncurses, considering it doesn't even require X-Windows. But I think you'll be fine if you just use GTK. Those running KDE can still use your program if they have the GTK runtime libraries installed; it just won't look like a KDE application.

---

### Post by nvteighen on 2010-04-24
> **Lux Perpetua said:**
> The most portable toolkit for building interfaces is probably ncurses, considering it doesn't even require X-Windows. But I think you'll be fine if you just use GTK. Those running KDE can still use your program if they have the GTK runtime libraries installed; it just won't look like a KDE application.

Well, you're right... I hadn't even thought about ncurses! :p

---

### Post by azagaros on 2010-04-24
wxWidgets... all platform lib...

---

### Post by Lux Perpetua on 2010-04-24
> **azagaros said:**
> wxWidgets... all platform lib...I might be missing something, but I'm not aware of any Qt backend for wxWidgets. KDE users would still need GTK. But wxWidgets seems like a smart choice if one considers Windows or Mac users among the user base.

---

### Post by vek on 2010-04-24
I'm working on a video library application, and picked Qt.  so far it has given me no issues - and runs on windows, mac, linux, (Gnome and KDE).  

I guess the difference is that WxWidgets is almost strictly a widget library for making the GUI, wheras QT is more like a platform library, encapsulating things like file reading, network, and database as well as widgets, so you don't have to write platform specific versions of each.  I liken it more to the .NET "platform", whereas Wx is more like just the gui part.  

Hope this info helps you choose.  It really depends on exactly what kind of project you're making.

---

### Post by Lux Perpetua on 2010-04-24
> **vek said:**
> I guess the difference is that WxWidgets is almost strictly a widget library for making the GUI, wheras QT is more like a platform library, encapsulating things like file reading, network, and database as well as widgets, so you don't have to write platform specific versions of each.  I liken it more to the .NET "platform", whereas Wx is more like just the gui part.  wxWidgets isn't just GUI; it has at least some of the other stuff you mentioned. I've never written for it, so I can't go into details there.

The point of wxWidgets, as I gather, is the look and feel: your application looks appropriate for the user's environment without having to port your whole source code. Of course, that's not completely true, since the user's environment needs to implement the wxWidgets API, and not all desktops have such implementations available. KDE seems to be an example.

---

### Post by Søren on 2010-04-25
I just realized that Java/ swing might be an obvious option as well. I think this works in Ruby and Python too?

Anyway I'll get started with gt and see how I go.

---

