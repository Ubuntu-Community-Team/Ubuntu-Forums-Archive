---
title: "Visual Studios-like programming tool"
date: 2009-08-23
forum: Programming Talk
---

### Post by HiImTye on 2009-08-23
Hi!

I'm looking to learn programming on Linux and was wondering if there are any tools for Linux that resemble Visual Studios for VB6? I have only dabbled in programming as a mild hobby and wrote simple programs to perform mundane tasks (mostly VB6/Win32API and a tiny little bit of C and alot of scripting in various forms (LUA, shell scripts, etc)). I realize that after switching to Linux I'm going to need to learn an entirely different language (most likely Python) but I'm looking for some tools to help me with some common tasks, namely form/window creation with a decent editor to get down to the nitty-gritty (important) parts.

any suggestions would be welcomed :)

---

### Post by hoboy on 2009-08-23
> **HiImTye said:**
> Hi!

I'm looking to learn programming on Linux and was wondering if there are any tools for Linux that resemble Visual Studios for VB6? I have only dabbled in programming as a mild hobby and wrote simple programs to perform mundane tasks (mostly VB6/Win32API and a tiny little bit of C and alot of scripting in various forms (LUA, shell scripts, etc)). I realize that after switching to Linux I'm going to need to learn an entirely different language (most likely Python) but I'm looking for some tools to help me with some common tasks, namely form/window creation with a decent editor to get down to the nitty-gritty (important) parts.

any suggestions would be welcomed :)

Well I think you should try monodevelop.
open console sudo apt-get install monodevelop.

---

### Post by bender1234 on 2009-08-23
Try Qt, Qt Designer isn't bad, though it's really only for making your widgets(windows) ui.
Must admit I just use a plain old editor myself.

---

### Post by shadylookin on 2009-08-23
mono supports visual basic(not sure which version). Also you can use C with linux.

---

### Post by ArmenianLeader4 on 2009-08-24
```
sudo apt-get install kompozer
```

it'll even recompile your scripts to look neater.
I just use gedit for most of my stuff, but thats the best second

---

### Post by HiImTye on 2009-08-24
is mono for python? I'm looking to try and stay away from primarily windows-based languages and I'm sort of intimidated by C, at least for now.

I understand that Qt doesn't skin well with gnome settings so I'm sort of leery about using Qt

is Komposer for the KDE framework? the name sort of suggests that it is

---

### Post by HiImTye on 2009-08-24
btw, Armenian, I like your signature

---

### Post by OutOfReach on 2009-08-24
> **HiImTye said:**
> is mono for python? I'm looking to try and stay away from primarily windows-based languages and I'm sort of intimidated by C, at least for now.

I understand that Qt doesn't skin well with gnome settings so I'm sort of leery about using Qt

is Komposer for the KDE framework? the name sort of suggests that it is

Mono is for .NET languages, like Visual Basic, C#, etc.
Python is a totally different language, and it works cross-platform.

C isn't so bad :), but yes for a beginner language I recommend learning something easier.

Who says Qt can't look nice on GNOME? QGtkStyle uses GNOME's theme on Qt apps and they blend in nicely.

Actually, I think Kompozer is GTK based, so no it's not built upon Qt/KDE libraries.

---

### Post by ad_267 on 2009-08-24
Kompozer is built using QT and is for designing web pages so you probably don't want that.

Monodevelop is the most like Visual studio out of all the Linux IDEs and is geared towards development in C# and .NET/Mono. While C# and .NET are very Microsoft oriented, there's actually quite a few applications that are built with Mono in Ubuntu. Banshee, F-Spot, Tomboy and Gnome-Do are some.

If you want to program GTK applications in Python or C there's a good tutorial at [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html). It focuses on using Glade 3 for interface design. Unfortunately it's never been completely finished off but it's a good start. You'll probably want to learn some basic command line only Python first though.

Most QT development is in C++, although Nokia has just recently announced PySide, Python bindings for QT. There is already the PyQT bindings but PySide will be improved and will be licensed under the LGPL, so hopefully Python will be used a lot more for QT development soon.

---

### Post by pepperphd on 2009-08-24
> **HiImTye said:**
> is mono for python? I'm looking to try and stay away from primarily windows-based languages and I'm sort of intimidated by C, at least for now.

I understand that Qt doesn't skin well with gnome settings so I'm sort of leery about using Qt

is Komposer for the KDE framework? the name sort of suggests that it is

Ubuntu is very dependent on Python, while Windows is not. So I'd have trouble calling Python a primarily windows-based language.  To be honest you are better off learning how to manually piece together your programs with a text editor and the command line.  I used to really push Kdevelop around here as a great IDE, which it is, but it doesn't stand up in power to the command line.

---

### Post by Major_Kong on 2009-08-24
> **pepperphd said:**
> Ubuntu is very dependent on Python, while Windows is not. So I'd have trouble calling Python a primarily windows-based language.  To be honest you are better off learning how to manually piece together your programs with a text editor and the command line.  I used to really push Kdevelop around here as a great IDE, which it is, but it doesn't stand up in power to the command line.

That hardly is always true... especially if we're talking about building guis.

---

### Post by HiImTye on 2009-08-25
> **pepperphd said:**
> Ubuntu is very dependent on Python, while Windows is not. So I'd have trouble calling Python a primarily windows-based language.  To be honest you are better off learning how to manually piece together your programs with a text editor and the command line.  I used to really push Kdevelop around here as a great IDE, which it is, but it doesn't stand up in power to the command line.
I wasn't calling Python a primarily windows based language, I was calling VB a primarily windows based language. I want to try to stay away from those :D

thank you for all of your suggestions, I have alot to work off of now :D

---

### Post by moster on 2009-08-26
I am impressed with [Gambas]("http://gambas.sourceforge.net/en/main.html"). It is VERY similar to visual basic. I would like to hear from more experienced programmers what they think of it. For now, it seems to me like a perfect RAD tool.

Similar is Lazarus, who is RAD tool based on free pascal. It is something like Delphi.

---

### Post by resander on 2009-08-26
Try the code::blocks (codeblocks) IDE. It works with several high-level languages and is available on Windows and possibly Mac too.
I think it is available via synaptic.

---

### Post by schmendrick on 2009-08-26
> **pepperphd said:**
>  To be honest you are better off learning how to manually piece together your programs with a text editor and the command line.  I used to really push Kdevelop around here as a great IDE, which it is, but it doesn't stand up in power to the command line.



i disagree. 
you dont need to know the toolchain (which a good IDE perfectly hides) to learn programming / get better at programming / learn a language.

i'd say learning what goes on BEHIND the scenes is something for later on, when you already have a grasp about how you can program.



as for the initial question:

i would also go for monodevelop or for qt creator.
with both you can easily create GUIs and both are the closest thing you can get to Visual Studio.

---

### Post by jjalocha on 2009-08-26
I usually use Python, and with simple text editor + bash, that is. In my opinion, it's a beautiful and powerful language for beginners. For creating both command-line, and GUI tools.

But I heard very good comments about the Python + Eclipse development environment:
[http://pydev.sourceforge.net/](http://pydev.sourceforge.net/)

---

### Post by Mirge on 2009-08-26
> **jjalocha said:**
> I usually use Python, and with simple text editor + bash, that is. In my opinion, it's a beautiful and powerful language for beginners. For creating both command-line, and GUI tools.

But I heard very good comments about the Python + Eclipse development environment:
[http://pydev.sourceforge.net/](http://pydev.sourceforge.net/)

Python so far me to me seems like a pretty decent language, especially well suited for beginners. I'd recommend it.

As for Pydev, I'm a huge Eclipse fan so naturally I tried Pydev before anything else. It works pretty well from what I can tell (nothing complex has been written by me)... my only small annoyance is when I have a syntax error, it underlines it with red and puts a circle X before line numbers... which is good, but after I correct the error, the X goes away but sometimes leaves the red line. Closing & re-opening file resolves it and it's not a big deal, but does get annoying.

---

### Post by Zugzwang on 2009-08-26
> **schmendrick said:**
> i disagree. 
you dont need to know the toolchain (which a good IDE perfectly hides) to learn programming / get better at programming / learn a language.

i'd say learning what goes on BEHIND the scenes is something for later on, when you already have a grasp about how you can program.


In theory, I would say that you are absolutely right. However, for development in Linux, I would say that this is not a very good advice. 

For example, beginners or advanced developers will at some point stumble upon instructions for including certain libraries in their project. Since there are multiple mechanisms to do so (pkgconfig, etc.) and doing so is different for every IDE, this is quite messy. In fact, there are hundreds of threads in this forum dealing with this thing and only in a few of them, the respective OP actually got to know how to link and include files correctly in their IDE of choice. Additionally, things tend to change with new versions of IDEs (and sometimes break, as for example with the autotools and kdevelop) and HOWTOs are almost always no longer up-to-date on the web. The only way around this problem is to know at least how to do it on the command line, writing custom Makefiles and by just using IDEs for debugging and quicker file browsind. This is why most people here will propose this - Whenever you have problems with your IDE or with compiling, people will be unable to find out where the problem is due to the different handling of things in different IDEs and will be unable to help since everone uses a different one.

---

### Post by schmendrick on 2009-08-27
> **Zugzwang said:**
> In theory, I would say that you are absolutely right. However, for development in Linux, I would say that this is not a very good advice. 

For example, beginners or advanced developers will at some point stumble upon instructions for including certain libraries in their project. Since there are multiple mechanisms to do so (pkgconfig, etc.) and doing so is different for every IDE, this is quite messy. In fact, there are hundreds of threads in this forum dealing with this thing and only in a few of them, the respective OP actually got to know how to link and include files correctly in their IDE of choice. Additionally, things tend to change with new versions of IDEs (and sometimes break, as for example with the autotools and kdevelop) and HOWTOs are almost always no longer up-to-date on the web. The only way around this problem is to know at least how to do it on the command line, writing custom Makefiles and by just using IDEs for debugging and quicker file browsind. This is why most people here will propose this - Whenever you have problems with your IDE or with compiling, people will be unable to find out where the problem is due to the different handling of things in different IDEs and will be unable to help since everone uses a different one.


good point zugzwang.

---

