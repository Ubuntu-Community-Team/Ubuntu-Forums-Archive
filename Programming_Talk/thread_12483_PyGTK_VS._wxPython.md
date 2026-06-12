---
title: "PyGTK VS. wxPython"
date: 2005-01-24
forum: Programming Talk
---

### Post by Quest-Master on 2005-01-24
These are both powerful and useful modules used when coding with Python to create advanced GUIs and front-ends for various applications. However, I've seen a lot of controversy on which one to actually use.

PyGTK comes pre-packaged with many distributions including Ubuntu; a huge plus there. wxPython can be installed in Ubuntu through apt-get; however, as a topic in Software Support shows ([http://www.ubuntuforums.org/showthread.php?t=12485](http://www.ubuntuforums.org/showthread.php?t=12485)), the wxPython in Warty still uses GTK1 which is extremely ugly and out-of-place. I truly hope Hoary has changed that.

wxPython is highly cross-platform, and the same code can be used across many systems with no additional work. PyGTK is as well, but looks quite alien on Windows. This can be fixed with some background and cosmetic work; a hassle to some. 
One thing to note is that both of these libraries use GTK on Linux; the actual coding done with them is different however. wxWidgets also directly calls on the Windows and OS X APIs just fine, which is most likely a good thing since this means your code works absolutely for the majority of desktop users perfectly. PyGTK uses GTK on all platforms which can either be regarded as a positive or negative aspect.

I've looked through many code examples, and wxPython seems to achieve the same effect that PyGTK does in much less time and fewer lines of code (around 20-25 lines for a Hello World program in PyGTK, and 10-15 in wxPython from what I've seen). 

PyGTK sports Glade, hailed as the number one GUI designer for Python. wxPython as many answers to this, including Boa Constructor and PythonCard, and the one and only wxGlade.

I'd like to see the opinions of the Ubuntu users here on which is superior in their eyes; wxPython or PyGTK? :) Let's keep it friendly and clean as well.

---

### Post by stateq2 on 2005-01-24
[QUOTE=Quest-Master]the wxPython in Warty still uses GTK1 which is extremely ugly and out-of-place. I truly hope Hoary has changed that.[/QUOTE]

I agree....gtk1 is ugly and should be dead.  btw, yes, hoary wxpython uses gtk2 :)

---

### Post by Quest-Master on 2005-01-24
[QUOTE=stateq2]hoary wxpython uses gtk2 :)[/QUOTE]

:D

I think it might be time to move.

---

### Post by Daniel G. Taylor on 2005-01-25
Just thought I'd add that wx is native in OSX, while pygtk (if you can get the latest version, good luck) requires X11 and doesn't fit well with the rest of the system.

That said, I can't get wxpython to work in OSX, and it caused some trouble last time I tried it in Hoary. I am comfortable with GTK+ development, and will stick to pygtk for now!

I'd be willing to help pay for a port of GTK+ to OSX is they could make it use the native widgets. You'd think with Apple getting more popular again some work would be put into this.

Also, how did you get wx for Windows? I must have missed the binaries... (I'm just curious, don't actually have any Windows systems)

---

### Post by Quest-Master on 2005-01-25
There are downloads for it on the main wx site. wxPython also has an installer for Windows.

wx is technically faster since, as you said, it makes native calls on OS X and Windows and GTK on Linux which isn't exactly native, but looks perfect with any desktop environment (KDE, Gnome, XFCE, and so on).

---

### Post by Alessio on 2005-01-25
[QUOTE=Quest-Master]There are downloads for it on the main wx site. wxPython also has an installer for Windows.

wx is technically faster since, as you said, it makes native calls on OS X and Windows and GTK on Linux which isn't exactly native, but looks perfect with any desktop environment (KDE, Gnome, XFCE, and so on).[/QUOTE]
 This discussion is very interesting! Do you tell me to learn pyGTK o WXPython? For multi-platform code?

---

### Post by Quest-Master on 2005-01-25
[www.wxpython.org](www.wxpython.org) for wxPython. All code works fine multi-platform.

[www.pygtk.org](www.pygtk.org) for PyGTK. A bit of tweaking needed to LOOK native on Win32, and no idea about the OS X port.

---

### Post by stateq2 on 2005-01-26
[QUOTE=Alessio]This discussion is very interesting! Do you tell me to learn pyGTK o WXPython? For multi-platform code?[/QUOTE]
for multiplatform code, I suggest wxpython.  If you're only doing it for linux/bsd, pygtk is ok...although I'd still use wxpython  :-)

---

### Post by Daniel G. Taylor on 2005-01-29
On OSX GTK+ (and so pygtk) is anything but native looking or acting, if you can even get it working. Any GTK+ applications will also need an X11 server running (Apple provides an accelerated X server called X11.app that works great).

Also, there are some things you will need to do to make sure that your code does indeed work fine across multiple platforms (some functions are only available for certain systems, for example). GUI-wise wx works on all systems, but there is more to an application than its GUI.

---

