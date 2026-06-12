---
title: "I would like a hint about GUI choice."
date: 2012-08-21
forum: Programming Talk
---

### Post by ryantierp on 2012-08-21
Hi

I'm in the process of developing a in car entertainment centre with small screens, makes it easier to drive if you also see where your going. But that leaves me with little screen real estate so an ordinary desktop is impractical. So what I want to do is to start all applications via a interface that reminds of what small gps's uses. list or a few buttons in columns.

In short, it should only act as a launcher central.

But i'm stuck due to the amount of available choices and the fact that last time I programmed something, BASIC was considered top of the line after LISP.....

What is the best way to make an interface that lets a user start a application with just a touch on the touch-screen?

Best Regards

---

### Post by trent.josephsen on 2012-08-21
That's going to be dictated by your hardware, and operating system, if you're running one. Is this an... embedded Ubuntu system, or what?

---

### Post by jibawakee on 2012-08-21
ANDROID?!?!?!?!?!?!?!??!?! idk its runs on embedded systems and can be used in small and compact hardware ):P:p

---

### Post by ryantierp on 2012-08-21
I'm running openbox on ubuntu. The hardware is Intel Atom2700MUD.
Android is going to be used for the other seats in the car but the head unit are used for , multimedia, navigation and server for the rest of the users.

---

### Post by trent.josephsen on 2012-08-21
On a full X11 stack? That's a bit heavy...

With that setup in mind, I don't see why this should be significantly different from any ordinary desktop application, so long as touchpad presses are translated into mouse clicks. My default choice would be Python, which is also useful for scripting openbox and could provide some nice flexibility. Python is easy to pick up and generally easy to create GUIs in, although the details depend on the toolkit. When it comes to toolkits, most if not all of the most popular ones have bindings for Python.

That's if Python is already installed, or if you have the authority and free space to install it. You might look into Java for something similar in terms of overhead that's a little more widespread. (Not that Python is by any means rare, even on embedded platforms.) Personally I just don't like Java as a language, which is why it wouldn't be my first choice. It's fast though, and pretty easy to create GUIs in once you're up to speed with the language.

If Python or the JVM is just too big to deal with on your system, then you'll be down to writing something in C or C++ with one of the toolkits already mentioned, perhaps Gtk or QT respectively. C versus C++ is a perennial holy war so I'll just say I'm normally on the C side, but both would probably work perfectly fine for your application; if you want more information on why someone would choose C over C++ or vice versa, I encourage you to search these forums.

Regarding GUI toolkits. If you choose Java you'll likely want to use the standard Swing toolkit, which is ugly as all get out but whatever. Otherwise you have a choice of many toolkits; Gtk, QT, Tk, FLTK, and wxWidgets come to mind. Some of these (FLTK, Tk) are more basic and lightweight, while some (Gtk, QT) are more full-featured and heavy. Again, if you search the forums you'll find many discussions about the relative merits of different GUI toolkits. One thing you may keep in mind is that your embedded system probably already has at least one of Gtk and QT installed just to run whatever other applications it has[1], and so choosing a more lightweight but less common toolkit may actually take more overhead than using the heavyweight toolkit that's already installed.

[1] Unless the other apps to run on this device are statically linked.

---

### Post by ryantierp on 2012-08-21
I have considered python since it seems somewhat easier to pick up then Java. So that will probably be my choice with Glade for the GUI part. The hardware actually performs rather above my expectations with a few exeptions. The graphic struggles with full HD and Ubuntu does not support Hibernation when using SSD disk. Otherwise, I'm satisfied with the hardware.

When fully functional I will put the complete system on a diet and purge everything unnecessary. My goal is to be able to fit everything on a USB stick for easy distribution. 

I really do appreciate your inputs, thank you !

---

### Post by lykwydchykyn on 2012-08-21
I have an open-source project written in python + QT that is basically a full-screen, themeable, configurable launcher.  I don't know if it might give you ideas or be a starting point for what you need, but check it out if you want to:

[http://github.com/alandmoore/KiLauncher](http://github.com/alandmoore/KiLauncher)

---

### Post by ryantierp on 2012-08-21
I will definitely take a look at your solution, sounds like it might be what I need to get started. Thanks!

---

