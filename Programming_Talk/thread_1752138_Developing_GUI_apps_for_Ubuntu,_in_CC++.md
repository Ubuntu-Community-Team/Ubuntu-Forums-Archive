---
title: "Developing GUI apps for Ubuntu, in C/C++"
date: 2011-05-07
forum: Programming Talk
---

### Post by farproc on 2011-05-07
I am familiar with developing GUI applications for both Windows and MacOS, using the Windows API and Objective-C based Cocoa framework respectively.

Now, I want to try my hand at the Linux platform, via Ubuntu. Given that I am familiar with XCode on the Mac and Visual Studio on Windows, what do I need to install on Ubuntu to get started developing simple GUI apps in C/C++.

Ive started by installing Code::Blocks and GTK+ - however, while both Windows and MacOS have a very definite idea of their being a system provided windowing/control/widget library, its less obvious to me which widget library I should be using on Linux, or Ubuntu specifically.

The buttons in my first GTK+ application were distinctly different from the buttons in the various Ubuntu desktop utilities. Ive avoided using QT or Wx so far because - on Mac and Windows - its always been important to me that I use the systems look and feel library as much as possible.

What do I need to develop in to get my apps using the Ubuntu 11.4 buttons, and magic scrollbars (for example)?

---

### Post by simeon87 on 2011-05-07
I'm developing an application in GTK+ and the buttons don't look different compared to other applications on Ubuntu? Could it be that you are using certain settings that causes them to be different?

---

### Post by farproc on 2011-05-07
No idea. lol. I'm not even sure if I should be using gtk+2 or gtk+3

---

### Post by simeon87 on 2011-05-07
> **farproc said:**
> No idea. lol. I'm not even sure if I should be using gtk+2 or gtk+3

Most Ubuntu installations will have 2 because 3 is very new (it was released a few months ago). I'm sure GTK+3 will be included in the latest Ubuntu edition so that developers can start developing for it.

I must say I'm not running 11.04 and that version is using [Unity]("http://unity.ubuntu.com") so it could be that things have changed due to that.

I'm not sure what to say because C/C++ and Gtk+ should be sufficient to develop an application. Can you post a screenshot of the GUI that you've seeing? Many Ubuntu applications are using Gtk+ so that shouldn't be it.

---

### Post by r-senior on 2011-05-07
> **simeon87 said:**
> I must say I'm not running 11.04 and that version is using [Unity]("http://unity.ubuntu.com") so it could be that things have changed due to that.
I'm running 11.04/Unity and I've been playing around with C/Gtk+2 off and on over the last couple of weeks. Everything looks like it should and is consistent with other applications (including overlay scrollbars).

---

### Post by farproc on 2011-05-07
I just found developer.ubuntu.com - should have looked for that earlier. I'll retry with Anjuta & GTK 2

---

### Post by nvteighen on 2011-05-07
In GNU/Linux, everything is very modular, so it's a bit different... In the first place, there's no such thing as a "system look and feel". Desktop Environments determine a default library they like for their official apps (KDE, Qt; GNOME, GTK+), but nothing prevents you to use any X11-based widget toolkit in any X11-based Desktop Environment. Try installing Amarok and lauch it from GNOME; APT will grab Qt as a dependency and Amarok will work flawlessly despite being a "KDE application". Of course it won't look integrated to the desktop.

---

### Post by Jonas thomas on 2011-05-07
> **farproc said:**
> 
The buttons in my first GTK+ application were distinctly different from the buttons in the various Ubuntu desktop utilities. Ive avoided using QT or Wx so far because - on Mac and Windows - its always been important to me that I use the systems look and feel library as much as possible.

I believe that Qt widgets are not native to the OS, but I believe that WX is basically a wrapper to the native widget.

[http://www.wxwidgets.org/]("http://www.wxwidgets.org/")
> wxWidgets is a C++ library that lets developers create applications for Windows, OS X, Linux and UNIX on 32-bit and 64-bit architectures as well as several mobile platforms including Windows Mobile, iPhone SDK and embedded GTK+. It has popular language bindings for Python, Perl, Ruby and many other languages. **Unlike other cross-platform toolkits, wxWidgets gives its applications a truly native look and feel because it uses the platform's native API rather than emulating the GUI.** It's also extensive, free, open-source and mature.


---

### Post by SledgeHammer_999 on 2011-05-07
Except that in Linux there is no such thing as "native" widget toolkit...

Sure in Ubuntu the "native" toolkit is Gtk+, but in Kubuntu the "native" toolkit is Qt.
But this doesn't really matter. Read **nvteighen**'s post.

@farproc
If you have any problems please ask and post some code too.
Also in case you're going with C++ I recommend using [Gtkmm](www.gtkmm.org) instead of Gtk+ directly.

---

### Post by teachop on 2011-05-07
Don't fear Qt.  In my experience Qt does a good job looking fairly natural on various platforms.  The IDE Qt Creator is nice and clean C++ environment, I really like working in it.  Hope Nokia thrashing won't hurt the long term viability, but right now when I have to put out a cross-platform utility, I use Qt Creator.

---

### Post by mmix on 2011-05-07
try vala
[http://live.gnome.org/Vala](http://live.gnome.org/Vala)

---

### Post by farproc on 2011-05-08
> **nvteighen said:**
> In GNU/Linux, everything is very modular, so it's a bit different... In the first place, there's no such thing as a "system look and feel". Desktop Environments determine a default library they like for their official apps (KDE, Qt; GNOME, GTK+), but nothing prevents you to use any X11-based widget toolkit in any X11-based Desktop Environment. Try installing Amarok and lauch it from GNOME; APT will grab Qt as a dependency and Amarok will work flawlessly despite being a "KDE application". Of course it won't look integrated to the desktop.

I find that somewhat unfortunate. If I develop a program for Windows 95 using the windows common controls, each version of the OS I run, it will display using the appropriate widget set to appear integrated with that desktop.

If I wish to write an application now for Ubuntu how can I expect it to remain integrated with future updates to the Ubuntu desktop - or am I committed to rebuilding it for each Ubuntu release?

In my windows development environment, I (professionally) develop an application that runs on Windows 2000, XP, Vista and Windows 7 - from a single binary it displays the look and feel appropriate to the OS version its run on.

I would like to achieve a similar result in Ubuntu - I would target, probably, 10.04, but I would want it to appear integrated with the desktop environment of at least 10.4, 10.10, 11.4 and 11.10 for now.

---

### Post by SledgeHammer_999 on 2011-05-08
Then go with Gtk+ if you want to target Ubuntu. Although Qt apps don't look horrible in a Gtk+ environment. Moreover, some of them (eg qbittorrent) can you use a "gtk style/engine" that effectively makes them look native in a Gtk+ environment because they use the currently selected Gtk theme to draw their widgets.

Don't be so concerned about look and feel when choosing between Qt and Gtk+. 
I suggest you install some qt apps in your Ubuntu so you can examine you they "look and feel" under Gnome.

---

### Post by nvteighen on 2011-05-08
> **farproc said:**
> I find that somewhat unfortunate. If I develop a program for Windows 95 using the windows common controls, each version of the OS I run, it will display using the appropriate widget set to appear integrated with that desktop.

If I wish to write an application now for Ubuntu how can I expect it to remain integrated with future updates to the Ubuntu desktop - or am I committed to rebuilding it for each Ubuntu release?

In my windows development environment, I (professionally) develop an application that runs on Windows 2000, XP, Vista and Windows 7 - from a single binary it displays the look and feel appropriate to the OS version its run on.

I would like to achieve a similar result in Ubuntu - I would target, probably, 10.04, but I would want it to appear integrated with the desktop environment of at least 10.4, 10.10, 11.4 and 11.10 for now.

No problem, as long as you use the same major version of GTK+. Get a GTK+ 1.x application (there are still some in the repos) and you'll se how bad it will look in GNOME 2.x :D. 

In general, in GNU/Linux development you actually target for libraries, rather than OS-es; of course, OS-es ship one or multiple versions of libraries, so you may say you're targeting some OS indirectly. That's why projects have a "dependency list" rather than a statament like "Compatible with <insert distro>". Those dependency lists usually say things like "This project uses: libwhatever (version >= 3.1), fancy-something (version 1.2), etc.". As you surely knoe, the Debian packaging system tries to guarrantee satisfaction of dependencies programatically.

GTK+ is a widespread and key system library for a vast number of distros, you can be sure that GTK+ 2.x will always be available. You can be pretty sure that as long as GNOME 2.x is running, your program will look perfectly integrated (look and feel will vary depending on the Theme the user has chosen, but this also occurs in Windows).

---

### Post by teachop on 2011-05-08
> **SledgeHammer_999 said:**
> TQt apps don't look horrible in a Gtk+ environment.
I just pulled up a simple dialog box application created in Qt with Qt Creator a couple weeks ago to configure Xbee radios from a USB port.  Put it along side several other program dialog boxes, and some apps from the System Settings Control Center that I opened just to compare.  They look like they belong together, no warts at all.  This is on Ubuntu 11.04 Unity.

---

