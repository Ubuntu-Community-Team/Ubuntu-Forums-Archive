---
title: "Coming from c#/vb Windows Forms IDE - which is my best plan of attack?"
date: 2010-04-12
forum: Programming Talk
---

### Post by dchurch24 on 2010-04-12
Hi all,

As the title suggests, I am a Windows programmer - I primarily use C# and some Vb.net.

I have written Python scripts for XBMC and have used python to create terminal apps to control my lights/doors etc... via relays and switches.

I've used Java/J2EE/J2ME, a little Perl, and a little z80 asm over the years.

I take to new languages quite quickly - although I've really only used 'managed code' in anger.

I'd like to start designing GUI apps for Ubuntu, but am unsure of the best language/IDE etc...

C seems like a decent start, or maybe Python - but I have no idea how to create a GUI really without Visual Studio ;-)

I have tried to use GTK+ but found that I really couldn't get on with it.

Is there a Visual C equivilent?

If not, what would anyone suggest for a 'managed coder' to become a 'real coder'?

---

### Post by phrostbyte on 2010-04-12
MonoDevelop lets you code up Linux apps in C#, if you are used to Visual Studio you should find the interface to be somewhat familiar.

Click for download:
[apt://monodevelop,mono-devel]("apt://monodevelop,mono-devel")

You can also do all GUI development in Python if you prefer that, Python is very commonly used in Ubuntu for GUI via PyGtk and there are tools like "Quickly" that make it pretty easy. 

If you want to do unmanaged devel (eg: C++), KDE is almost entirely C++. C++ makes memory management a bit easier then C (imo) because of smart pointers and destructors.

---

### Post by dwarfolo on 2010-04-12
You can try anjuta + glade

[http://www.anjuta.org/](http://www.anjuta.org/)

Or you can use PyGTK + glade if you prefer python.

If you want to save your experiece with C# you can check Mono and GtkSharp

[http://www.mono-project.com/GtkSharp](http://www.mono-project.com/GtkSharp)

---

### Post by dchurch24 on 2010-04-12
Hi, wow!

Thanks for the quick replied!

I'd forgotten about mono!

That does seem like the obvious choice for a .net programmer ;-)

I'm just downloading NetBeans - I used to use that when doing J2EE programming for a company some years ago.

When that's finished (I have a reeeeaaaallly slow Internet connection), I'll have a look at MonoDevelop.

Thanks guys, much appreciated!

---

### Post by azagaros on 2010-04-12
Laying it out for you...

I may suggest you pick a language first.  Java is out there and relevant to do coding like you want to do on both Windows and Linux platforms.  I am not sure about OS X(mac) but I assume its there too.

Forms based Ide on Linux is Lazarus (Delphi/Object Pascal variant) or XBasic (a basic variant not like VB)

Gui Programming can be accomplished through c++, c, python and a few others.. The tools to accomplish the graphic side of user interfaces vary to taste and I end up coding with out them.

wxWidgets library for c++ and python, and supposedly a c# variant is in the works.  It also has tools for Form based programming like those of Visual c++, c# and Basic.  But it is a Library.  It has a great forum for general help with the library.

Gtk for C and Gtk++ for C++ are the main back bone for Gnome and QT is the backbone of KDE.  They are libraries and each have a set of tools to do some work for them.

IDEs out there are: 
eclipse(java and others)
Code::blocks (generally c++, using wxWidgets)
NetBeans(java and others)
Code Lite(generally c++, using wxWidgets)
Lazarus(Delphi/object pascal)

They all use a compiler or Runtime module to get tasks done or to get code to run.  I may have missed a few.  I hope I put something into focus first.

---

### Post by dchurch24 on 2010-04-12
Again, wow!

Thanks for the exhaustive reply - much appreciated.

Lazarus looks good, although I've never really used Pascal since school - I've always considered it a teaching tool and little more. I suppose it's come on a lot since those days!

Hey, learning is fun - I'll give all of the above a go and see which suits my style best!

My thanks to all.

---

### Post by phrostbyte on 2010-04-12
There is many different WYSIWYG GUI designers around.

Glade is the "epic" one for Gnome, and supports many many many languages. (Eg: C, C++, Python), most "major" IDEs integrate with Glade in some way, to provide its functionality. Quickly also integrates with Glade.

MonoDevelop has it's own Gtk+ (Gtk#) GUI designer. Very similar to Visual Studio WinForms in function.

NetBeans has a Swing GUI designer. (Java)

Qt Creator (IDE) includes a Qt GUI designer. (C++)

Qt Designer is like the "Glade" of Qt, and supports languages other then C++.

Gambas is a VB6 like IDE, with designer.

That's just a shortlist. :)

---

