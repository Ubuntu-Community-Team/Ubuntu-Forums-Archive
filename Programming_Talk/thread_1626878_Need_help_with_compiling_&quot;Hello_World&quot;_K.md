---
title: "Need help with compiling &quot;Hello World&quot; KDE App"
date: 2010-11-20
forum: Programming Talk
---

### Post by wiseguy12851 on 2010-11-20
I gave up after 2 hours of trying to compile a simple Hello World app using the KDE architecture. Gnome is very easy and straightforward to code for, simply include a list of headers. KDE, however, appears to require both the headers and a cmake script.

I am using eclipse, the tutorial to configure eclipse requires checking out a project and making it, then importing it into eclipse... The instruction on making the other project are far beyond complex and even then you don't know how to setup eclipse for your projects.

eclipse can't find any of the KDE includes, I am beyond lost and don't know where to begin, I love KDE but it's by far the most difficult architecture I've ever seen for compiling programs on.

Help much appreciated, Gnome is based on the C language and I chose KDE because it's in C++.

---

### Post by GeneralZod on 2010-11-21
It's not clear which "tutorial" you're using - have you read the KDE "Hello, world!" tutorial?

[http://techbase.kde.org/Development/Tutorials/First_program](http://techbase.kde.org/Development/Tutorials/First_program)

---

### Post by wiseguy12851 on 2010-11-21
Sorry for being too general, the link in your post to "First Program" is the one I am referring to. It's very complicated to setup.

Why can't I just tell eclipse the extra folders to search in for includes, libraries, etc... instead of going through cmake or a special program

---

### Post by nvteighen on 2010-11-21
What do you mean by "KDE development"? Is it just that you want your program have the look-and-feel of the standard KDE applications or that you're planning to develop a program that needs the KDE API e.g. to communicate with the Kicker or the notification system or any specific feature of the KDE desktop environment?

From your comments about "GNOME development", which sound more to comments about "GTK+ development", I think you want just to create a GUI that looks like the programs in KDE. In other words, you want to do "Qt development".

GTK+ and Qt are GUI toolkits, libraries to create GUIs and they're completely independent of their "respective" desktop environments. Think of GNOME as a collection of programs that chose GTK+ as their standard GUI toolkit because they liked it to have a uniform look-and-feel and KDE as a collection of programs that chose Qt for the same. But, you can run GTK+ programs in KDE and Qt programs in GNOME... Actually, they even work on Windows.

So, if you only want to create just a GUI, use this Qt tutorial: [http://doc.trolltech.com/4.3/tutorial.html](http://doc.trolltech.com/4.3/tutorial.html) (install the qt4.3-dev package).

Now, it's untrue that GTK+ is only available for C. If your *only* reason to switch to Qt is because you like C++ even though you like GTK+, then use the gtkmm binding, which is GTK+ for C++. Of course, if you also like Qt better (which is a very interesting library), keep using it.

---

### Post by GregBrannon on 2010-11-21
Your post reads more like a 'vent' than a request for help - and that's okay.  I understand your frustration, but you don't give a helper much info to go on.

Post your code (isolated to the problem area(s), if possible), provide a link the the tutorial you're using, a copy of the confusing/complicated instructions, and give specific error messages and/or the undesirable results you're experiencing.

Then count to 10, try deep breathing exercises (don't hyperventilate), and be patient while the excellent programming community on this forum rallies to help you get over this hump.

Good luck, and don't give up!

---

### Post by wiseguy12851 on 2010-11-21
Very helpful posts but I did start this thread last night so I'm not as frustrated as I was then.

I'm coming from a Windows programming background so I'm getting used to the Linux setup and it's technologies.

Yes I'm just wanting to create a typical GUI application, since I didn't fully understand the different technologies avaliable I though KDE programs had to be made using the KDE API and Gnome programs using the Gnome API. I assumed GTK+ and QT were about the same and similar to Microsoft's .NET in that it was portable but over simplified.

Since I desire to program advanced & professional programs rich with features and customizations I always avoid over-simplified architectures / languages like Microsoft's .NET and (by habit) go straight for the API programming

To wrap this up into a helpful post:
[LIST]
[*]Can QT offer anything I could get by going straight to the related API
[*]Are GTK+ and QT generally the same just developed by different projects
[*]Is QT and/or GTK+ what most people use, or what a proffesional application like GIMP, Eclipse, or VMware/Virtual Box would use
[/LIST]

I know I started this thread with a question on setting up Eclipse to compile KDE programs but know I'm slightly confused as to whether that's the right or typical choice most people choose and makes me wonder what others architectures are out there besides GTK+ and QT

---

### Post by Reiger on 2010-11-21
For developing with KDE you don't need C/C++, you could use Python or C# or something. For developing KDE apps with C/C++ you might want to look into Kdevelop which is an IDE the KDE guys apparently use themselves extensively -- purpose built for developing with KDE.

---

### Post by nvteighen on 2010-11-21
> **wiseguy12851 said:**
> 
To wrap this up into a helpful post:
[LIST]
[*]Can QT offer anything I could get by going straight to the related API
[*]Are GTK+ and QT generally the same just developed by different projects
[*]Is QT and/or GTK+ what most people use, or what a proffesional application like GIMP, Eclipse, or VMware/Virtual Box would use
[/LIST]


[LIST]
[*]I don't understand what you refer to with "related API". Could you elaborate?
[*]Well, it's a long story related to licensing. Qt wasn't open source at the beginning and that forced the Free Software Foundation to develop GTK+ as an alternative. In time, Qt became GPL and the problem of licensing was solved, but GTK+ was already there and it became more a matter of taste (and in part, C vs. C++). But yes, both are essentially the same and feature the same power and even similar ways of doing things. Qt offers some additional stuff that nowadays is part of Standard C++ that wasn't there when Qt was initially created.
[*]Heh... GTK+ was created from GIMP :D And Qt was a comercial library initially and now is used by Nokia in their Symbian OS, for example. If I'm not mistaken, Skype uses Qt too even in its Windows version. Yes, people use these toolkits quite a lot.
[/LIST]

By the way, GTK+ and Qt are libraries, not "architectures" nor platforms. They don't interpret code like the Microsoft .NET Framework...

---

### Post by wiseguy12851 on 2010-11-21
Very helpful post, here's the answer to your first question:

By related API I meant the actual Gnome or KDE API, Can I access any API features - not necessarily API calls but produce the same effect or outcome as if I had gone directly to the Gnome/KDE API themselves

I'm not familiar with KDE or Gnome quite that well so I'll give a similar Windows example to clarify what I'm talking about above:

I can go to the STL library and easily write a file in Windows in ascii or binary, but If I go directly to the Windows API I have several extra pages of options for absolute control over how I want the file to be output and more.

With that said does the Qt and/or GTK+ closely mimic most of the features of whatever underlying API is there whether it's Windows/Gnome/KDE or does it leave out/simplify a lot of the API that I could have had more control over If I had just chosen a specific API

---

