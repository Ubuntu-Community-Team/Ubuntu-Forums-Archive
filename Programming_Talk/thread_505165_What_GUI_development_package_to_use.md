---
title: "What GUI development package to use?"
date: 2007-07-20
forum: Programming Talk
---

### Post by DaveAK on 2007-07-20
I'm making the switch from Windows to Ubuntu but don't know where to get started to replace my VB.NET IDE.  I'm a good programmer, not cutting edge stuff, and nothing commercial anymore.  I have a home app that I want to rewrite and I really don't mind what language it's in.  If I don't know it I'll learn it.  I do need something that will help me with GUI layout/design though, and I'd much prefer an IDE, although combinations of IDE and command line would work.  I'm just using a standard Ubuntu Feisty install.

So, what do you guys suggest? :)

---

### Post by leibowitz on 2007-07-20
It's hard to say something that will please you. So feel free to listen to everyone and try all of those for yourself.

I will not propose anything, but will say what I did feel with using some of those IDE.

First thing I installed on my linux box : Kdevelop. This is big, huge, many buttons everywhere and I don't know any C++. So that's kind of dumb what I did (to install this). That was too big for me.

Then I tried everything with Qt or Kde name in it. Still nothing interesting in those.

Then I learned about Gambas (a basic IDE) and install it. Within one week I can do a small GUI and I learned the basic language. Which is great within one week. It's really easy to use.

But... after some month, this application seems like breaking on every release. It's hard to install nor update, and doesn't feel right for many application. I will never again install this, I think.

Then I learned the C. C is great. C is hard, but is great. With C you can do everything (like writing a kernel...) but you need times.... more times than Basic to do the same ****.

Now like many developers I'm using text editor to develop. I just need the Documentation API on a side, but a text editor is sufficent.

I should mention that for C++/Java and OO language it's better to use an IDE. Java has many, and Eclipse is good for many language I think. I don't use it, but I need to say it's something really usefull but will not help you to build GUIs. 

So you should better choose one of those Java IDE available (choose between Sun or IBM). And go for it, but you will need to learn Java and thus OO.

Anyway, Basic is not going to help to learn "how it works". When you did learned how it works underneath the IDE, then everything is good enough to develop.

It may takes years to learn all that stuff. Though it depends on the language you choose.


I would resume all of this in one sentence: choose a language first, not the IDE.

---

### Post by cb951303 on 2007-07-20
.NET + MonoDevelop(Use the latest version for integreated GUI designer)
C + Glade

---

### Post by ankursethi on 2007-07-20
Okay, here's a list of suggestions you're likely to get.

1. C++ with KDevelop/Anjuta/Eclipse/Geany using the Qt/GTKMM toolkit.
2. Python with IDLE/DrPython/SPE/Eric using the PyGTK/PyQT/Tkinter/wxPython toolkit.
3. C with KDevelop/Anjuta/Geany/Eclipse using the GTK+ toolkit.
4. Ruby with some obscure IDE and some obscure GUI toolkit (sorry, I don't know Ruby).
5. Perl with some obscure IDE and some obscure toolkit (don't know too much Perl either).
6. "Use a goddamned text editor and the commandline to compile the programs. You don't need anything else." style comments, which quickly become flamewars (IDEs vs. text editors, Emacs vs Vi etc.).
7. C# with Monodevelop and GTK# GUI toolkit.
8. Java with some obscure IDE (most likely Eclipse) and some obscure GUI toolkit (I'm no Java expert).

Here's what I use :
Language : Python
IDE : DrPython
GUI Toolkit : PyGTK

I love what I use, because I spent so much time looking for something that fit into my programming habits, and this was it. I also program C/C++ ocassionally, but then I prefer a text editor and commandline because I don't do big programs in it. I've also tried and loved Anjuta as an IDE.

---

### Post by pmasiar on 2007-07-20
Python is simple to start with, powerful to scale up to really tricky apps, popular (with nice friendly community), has lots of libraries for anything you may ever want, installed on any Linux distro, and crossplatfom to Win and Mac. I recommend it.  See forum's sticky and wiki in my sig for links.

It can be used for desktop apps (wxPython, Glade) or web-based apps (Django, TurboGears), and it can be better shell than bash.

SPE (Stani's Python Editor) is one of popular IDEs, and Stani develops SPE on Ubuntu :-) Decent IDE to start is IDLE - I use both :-)

---

### Post by msgyrd on 2007-07-20
Eclipse and Netbeans are the two I would look at, and focus primarily on Java.  Both are very robust, and probably the most feature-complete IDEs available. Netbeans will probably provide most of the features you're used to with VisualStudio.Net (code profiler, debugger, stepping through code and runtime values, etc).  Both IDEs also support C/C++ via modules/addons.  

Eclipse is open source (not GPL though), while Sun controls Netbeans, although it's still free, I'm not sure about it's licensing or code availability.


For Python, I really enjoyed using SPE + wxWidgets also.

---

### Post by DaveAK on 2007-07-20
Great answers guys, thanks.

Quick question.  To the trained eye could you spot what language had been used to write a particular app?  I.e. do they each have little quirks when it comes to developing a GUI?  (This is purely out of curiosity, don't really know why it popped in to my mind to ask :) )

---

### Post by pmasiar on 2007-07-21
Depends on the platform. Ie wxPython are just linked calls to same wxWidgets C library, so I would be surprised if it was possible to tell  wxPython wrappers from wxWidget original calls. 

You worry about non-problem:

Dont trouble troubles before troubles trouble you.

---

### Post by cb951303 on 2007-07-21
> **DaveAK said:**
> Great answers guys, thanks.

Quick question.  To the trained eye could you spot what language had been used to write a particular app?  I.e. do they each have little quirks when it comes to developing a GUI?  (This is purely out of curiosity, don't really know why it popped in to my mind to ask :) )

I believe most GNOME applications are written in python...

---

### Post by slavik on 2007-07-22
> **cb951303 said:**
> I believe most GNOME applications are written in python...
any ideas which?

as for gui dev ... I suggest gtk+, because glade3 is very nice and the 4 major languages (c, c++, perl, python) have bindings to libglade.

---

### Post by Geekkit on 2007-07-22
Since this is such a personal choice-based request, remember that all replies you get are going to be based on each individual's experience, skill set, and preferences.

For me here's what I use:

Netbeans for:
[LIST]
[*]J2ME projects (for when I need  debugging, profiling, obfuscation abilities)
[*]C++ projects where I need UML diagrams (there's a C++ module as well as a UML module that you can get for Netbeans)
[*]J2EE projects (since Netbeans comes with Tomcat and makes it easy to start coding immediately)
[/LIST]

GEdit for:
[LIST]
[*]Straight C
[*]C++
[*]C with GTK+ (Glade 2 to generate the C code)
[*]XML
[*]XHTML
[*]CSS
[*]Javascript
[*]ActionScript
[*]Java
[/LIST]

For me right now I'm trying to acquaint myself with GTK+ and so what I've done is created my own makefile, C source code and header files and simply using GEdit and the terminal. When I know that I know the API calls and have time constraints I will switch over to an IDE or if I need some fancy features from an IDE such as obfuscation, heavy profiling features, and the ability to generate UML diagrams for documentation purposes.

My advice is to write down (or bookmark) the tools that everyone suggests in this thread and then try them yourself. That way you'll have a feel for what works for you. Remember, each answer here is "right" ... at least for that particular person. You'll find your "right" answer too ... hopefully.  :)

---

### Post by DaveAK on 2007-07-24
OK, so I'm going to try my hand at Python, using SPE.  It seems to have all I need to get started on my project.  Of course, I might decide to try anything else at anytime. :)

Thanks again for all your input. :)

---

