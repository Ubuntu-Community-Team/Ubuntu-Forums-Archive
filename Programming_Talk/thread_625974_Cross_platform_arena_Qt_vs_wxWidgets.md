---
title: "Cross platform arena: Qt vs wxWidgets"
date: 2007-11-28
forum: Programming Talk
---

### Post by Vadi on 2007-11-28
Hello,

I need to write a small app that'll essentially consists of a bunch of buttons, text labels, and other easy GUI functions. I need the app to be cross-platform though - so Linux, Mac, & Windows. I poked about the net, and it looks like my two options are either Qt, or wxWidgets. Gtk is sorta out of the question, because the user has to install it - my app will be way smaller than gtk itself. 

So, between Qt, and wxWidgets. I'm also helping to code for an oss project that's done in kde/qt, so I think qt will be the easier choice. However wxwidgets has an impressive number of apps in its belt, so it might be useful to learn too.

As you see I have no idea with which to start on. Can anyone who has had preferably experience, or knows a lot about both gui toolkits offer some advice?

Thank you.

---

### Post by smartbei on 2007-11-28
What language is the application in? For Python I would recommend using Tkinter, since that is included in Python itself.

If the application is 'way smaller' than GTK, it will also be way smaller than QT or wxWidgets, so I am not sure that that matters too much.

---

### Post by Vadi on 2007-11-28
Definitely not Python, since I don't know it at all. I'm familiar with C, learning C++ right now.

---

### Post by LaRoza on 2007-11-28
It looks like wxWidgets might be the best option for you.

---

### Post by Majorix on 2007-11-28
Isn't wxWidgets a library that also has to be separately installed on end-user's machine?

Programming GUI with C is horrible. Best of luck to you.

---

### Post by LaRoza on 2007-11-28
> **Majorix said:**
> Isn't wxWidgets a library that also has to be separately installed on end-user's machine?

Programming GUI with C is horrible. Best of luck to you.

I wouldn't say horrible, just less convenient.

---

### Post by Vadi on 2007-11-28
Wait, wait. Yes I am a complete newbie in the GUI arena. I thought I had to learn C++ for both languages?

---

### Post by Auria on 2007-11-28
Both C++ and wx are in C++. No idea why C was mentionned :)

I would just recommend you try them out, read their wikipedia entries, etc.

I personnaly use wxWidgets because :
1) I use Gnome and not KDE
2) I started compilling both at the same time and wx was done compilling first :lol:

Finally, depends what you're aiming for. For cross-platform, I like wx quite a lot. Uses underlying paltform code a lot, easy to distribute. If you're not going for cross-platform though, you should also consider GTKmm (if you aim for Gnome) or pure GTK if you really like C...

---

### Post by Vadi on 2007-11-28
One of the reqs is cross-platform. Because close to 99% of the people who'll be using it are on windows. And I'm on Ubuntu. But the other requirements are basic - just socket support, and basic GUI elements.

Having somewhat of a hard time compiling wxwidgets on both platforms though, as I mentioned in the thread on the forums there :/

---

### Post by LaRoza on 2007-11-28
> **Vadi said:**
> One of the reqs is cross-platform. Because close to 99% of the people who'll be using it are on windows. And I'm on Ubuntu. But the other requirements are basic - just socket support, and basic GUI elements.

Having somewhat of a hard time compiling wxwidgets on both platforms though, as I mentioned in the thread on the forums there :/

You should, IMO, write it in ANSI C or ANSI C++, then worry about the GUI.

---

### Post by Vadi on 2007-11-28
But the "backend" will be very simple. All it will be is just a socket that listens / sends commands, sending out when gui elements are used, or activating the gui elements when a command is received.

How can I go about hooking up the C code to a gui though? From the looks of it, it's all C++.

Thank you for your help, by the way.

---

### Post by samjh on 2007-11-28
[quote=Vadi]Definitely not Python, since I don't know it at all. I'm familiar with C, learning C++ right now.[/quote]If you're just learning C++, you probably won't be able to get much done with wxWidgets or QT.  Both tools are for C++, and GUI programming in C++ is not for beginners to the language.

Gtk is OK, and it is for C.  You don't need an installer for it.  Try to link GTK statically or distribute the shared binaries with your software.

Keep in mind that the wxWidgets runtime weighs in around 10 MB.  I'm not sure about QT, but it too will be substantial, if not bigger.  GTK would probably be the lightest of them all.

---

### Post by LaRoza on 2007-11-28
> **Vadi said:**
> But the "backend" will be very simple. All it will be is just a socket that listens / sends commands, sending out when gui elements are used, or activating the gui elements when a command is received.

How can I go about hooking up the C code to a gui though? From the looks of it, it's all C++.

Thank you for your help, by the way.

Write the functions for the app, use a simple text interface for testing, then use a GUI.

I would, if I had this goal of yours, do what I outlined above, then use the Windows API for Windows, GTK, QT or wxWidgets for Linux, and whatever a Mac uses (I would research this).

I would take the time to learn the other API's and use whatever tools are needed for them.

---

### Post by Vadi on 2007-11-29
:|

But the exact point of going Qt or wxWidgets was that so I wouldn't have to learn 3 API's. Nevermind that I've never used a mac, so I won't be able to test it there at all.

---

### Post by ZuLuuuuuu on 2007-11-29
> **Majorix said:**
> Isn't wxWidgets a library that also has to be separately installed on end-user's machine?

AFAIK, no, if you use C++ because it uses native API for all platforms. But if you are using a not-compiled language like Python, then yes, it has to be installed on end-user's machine.

---

### Post by samjh on 2007-11-29
> **ZuLuuuuuu said:**
> AFAIK, no, if you use C++ because it uses native API for all platforms. But if you are using a not-compiled language like Python, then yes, it has to be installed on end-user's machine.

It needs to be installed onto the end-user's machine, regardless of language: either by static linking or by including shared libraries with your application, or providing instructions to the end-user to install the libraries themselves.

Same goes for any library that is not installed when the operating system itself is installed.

wxWidgets calls native APIs to draw its widgets, but the wxWidgets library still needs to be present in either statically-linked or shared library form.

---

### Post by ZuLuuuuuu on 2007-11-29
> **samjh said:**
> It needs to be installed onto the end-user's machine, regardless of language: either by static linking or by including shared libraries with your application, or providing instructions to the end-user to install the libraries themselves.

Same goes for any library that is not installed when the operating system itself is installed.

wxWidgets calls native APIs to draw its widgets, but the wxWidgets library still needs to be present in either statically-linked or shared library form.

If you are distributing your wxWidgets & C++ application, the end-user do not have to install any other program than the program itself (especially if you statically linked the library while compiling, when it that case, you only need to give the .exe file and there is no installation at all).

But if you are using GTK & C then the end-user should install GTK runtime environment before using the application. And if you are using Python & wxWidgets then the end-user should install first Python, then wxPython to be able to use that program.

---

### Post by Vadi on 2007-11-29
What about Qt? Any installation needed if statically linked?

---

### Post by ZuLuuuuuu on 2007-11-29
I don't have much information actually if wxWidgets or Qt can be easily statically linked or whether it is the common way that people use. Maybe you should arrange program to use .dll files. But they are known that they don't need a runtime environment like GTK (which has its own advantages). So, if you use wxWidgets or Qt along with C++ then the users should install just your program and that's all. To give example behaviours: The most famous Windows software that uses Qt is I guess Opera web browser, and maybe we can give AVG anti-virus as a famous software example that uses wxWidgets.

But as far as I know there are some issues about Qt license on Windows platforms that prevents developers to use that library free on some conditions. I guess Qt developers here can give more information about that...

---

### Post by samjh on 2007-11-29
> **ZuLuuuuuu said:**
> If you are distributing your wxWidgets & C++ application, the end-user do not have to install any other program than the program itself (especially if you statically linked the library while compiling, when it that case, you only need to give the .exe file and there is no installation at all).

But if you are using GTK & C then the end-user should install GTK runtime environment before using the application. And if you are using Python & wxWidgets then the end-user should install first Python, then wxPython to be able to use that program.

I see what you mean now.  I thought you meant that wxWidgets & C++ don't need additional libraries, because your use of the work "install" seemed to use no particular context.

However, what you've said about GTK & C isn't correct.  If you have GTK sources and the libraries, you can link them statically or distribute them with your application.  The same as wxWidgets or QT.  I know there is an installation program for GTK, but that is not the only way to distribute GTK if you're a programmer.

---

### Post by ZuLuuuuuu on 2007-11-29
> **samjh said:**
> I see what you mean now.  I thought you meant that wxWidgets & C++ don't need additional libraries, because your use of the work "install" seemed to use no particular context.

However, what you've said about GTK & C isn't correct.  If you have GTK sources and the libraries, you can link them statically or distribute them with your application.  The same as wxWidgets or QT.  I know there is an installation program for GTK, but that is not the only way to distribute GTK if you're a programmer.

Sorry, I guess my English is not enough to understand your first paragraph :)

But I understand the second paragraph heh, yes I forget to add that you can also bind GTK as a static library but I talked as the most popular approach of developers/tutorials out there because I heared that if you bind GTK as statically then the software wents huge, example 7MB just to say hello world. I didn't tried that though...

---

### Post by samjh on 2007-11-30
> **ZuLuuuuuu said:**
> Sorry, I guess my English is not enough to understand your first paragraph :)Nevermind. :)

> But I understand the second paragraph heh, yes I forget to add that you can also bind GTK as a static library but I talked as the most popular approach of developers/tutorials out there because I heared that if you bind GTK as statically then the software wents huge, example 7MB just to say hello world. I didn't tried that though...

Yes it would be quite big.  But you have the same problem with wxWidgets and QT as well.  The wxWidgets shared library for Code::Blocks, for example, takes up a very large portion of the installation.

You don't need to statically link.  You can distribute them as shared libraries with your application.

If you don't understand what I'm saying, here's what I mean in simple terms:
[list]
[*]ALL widget libraries need to be distributed somehow, either as shared libraries or by static linking.
[*]It is the same for GTK, QT, wxWidgets, or anything else, because MS Windows does not include those libraries (the original poster is concerned mainly about MS Windows).
[*]So the issue of installing libraries or the size of executables after they've been statically linked, is not important.
[*]Because they all need to be distributed with the original poster's software regardless of which widget library he chooses.
[/list]

---

### Post by Vadi on 2007-11-30
Yep you nailed it.

I'm leaning towards Qt, since I'm learning it anyway for another KDE/Qt based project I'm helping to work on. But, someone mentioned iffiness with Qt on Windows. Does anybody have any experience with this?

---

### Post by Pharaoh Atem on 2009-02-10
The reason why Code::Block's wx library is so large is that they chose to do monolithic library building. For an IDE, this is ideal. However, in most apps, it is satisfactory to use the microlithic library style, where each section of wxWidgets is componentized into a separate library.

Qt is the same, although I believe they do not offer a monolithic library for their system. Qt4 has support for native widgets since 4.3.x I believe. And Qt 4.5 will have support for Mac's Cocoa API as well as Carbon.

In any case, if you want to implement all parts of it in a uniform cross-platform manner, I would suggest Qt 4.5. But, if your code has the backend split from the GUI/frontend, then I suggest wxWidgets, since it is easier to work with on componentized applications, in my opinion.

---

### Post by Vadi on 2009-02-10
This is an old topic. Since then, I realized that GTK is also cross-platform, and it's Glade designer for interfaces beats the Qt Designer and wxGlade hands down - so I went with it. Works great on both Linux and Windows.

---

### Post by bln102 on 2009-07-26
wxWidgets seems draw custom widgets (button, skins...) in native.

[http://wiki.wxwidgets.org/Painting_your_custom_control](http://wiki.wxwidgets.org/Painting_your_custom_control)
[http://wiki.wxwidgets.org/Drawing_on_a_panel_with_a_DC](http://wiki.wxwidgets.org/Drawing_on_a_panel_with_a_DC)

---

### Post by JordyD on 2009-07-26
> **bln102 said:**
> wxWidgets seems draw custom widgets (button, skins...) in native.

[http://wiki.wxwidgets.org/Painting_your_custom_control](http://wiki.wxwidgets.org/Painting_your_custom_control)
[http://wiki.wxwidgets.org/Drawing_on_a_panel_with_a_DC](http://wiki.wxwidgets.org/Drawing_on_a_panel_with_a_DC)

Actually, Qt now draws widgets using the native platform's toolkit as well. And I think it does a better job at it. When I use wxWidgets apps, I know they're wxWidgets apps. But when I use a Qt app, I can't tell.

This is how it works out (in my experience):
```

                   Windows              Mac             GNOME         KDE
GTK                not native*          not native*     native        native**
Qt                 native               native          native**      native
wxWidgets          native***            native***       native***     native***
```
* Can look native with proper theming
** IF you use a specific theming engine, and even then it looks a little out of place
*** Looks native most of the time, but has little quirks, like the toolbars not fitting in and windows not sizing correctly.

That said, Qt + C++ has more documentation, plus a neat IDE, so I prefer it.

---

### Post by pelle.k on 2009-07-26
Necromancing, are we?

Anyway, i'm very pleased with wxpython. Looks great as both as gtk and windows applications if you ask me. It can be a bit quirky at times. I'm not too fond of the API (wxpython) documentation though.
I'm using the latest wxformbuilder (from PPA) that does python code generation, so that's pretty comfortable.

I would be using PyQT4 if i didn't have to pay for the licence, should i decide to make a commercial app though. The C++ bindings are free to use in that situation, though. I'm just not very keen on leaving python just yet!

---

### Post by JordyD on 2009-07-26
> **pelle.k said:**
> Necromancing, are we?

They started it. :)

---

### Post by Vadi on 2009-07-27
I've stuck with GTK+ in the end. Looks okay on Windows (see latest Mono crusade posts), native on Mac (ported from X11), and Glade is much more usable than Qt Designer. Plus the level of support in #gtk is > #qt where the knowledgable people apparently don't hang out and you get suggestions like "try breaking the layout and redoing it again. helps sometimes".

---

### Post by Emanuele_Z on 2009-09-10
Hi, I have to design a GUI for an application (C++).
Now, I don't care about Windows ports (I'm developing in Linux naturally), but I would like to get the following:

- GTK like preferred (target Gnome enviornment)
- Ease of use as Java Swing

I'm using gtkmm at the moment, but the fact it uses pango for the labels/text and there's no real guide to it (or at least I haven't been able to find it yet...) is a bit depressing.

Naturally I don't want to use a plain C api, because I don't want to write 100 functions to deal with click/event blah blah, but I would like to inhert from virtual methods using, naturally, C++.

Is there any GUI api which has simplicity of Java Swing/AWT but is written in C++ against gtk?

What do you reccomend?

Cheers,

---

### Post by directhex on 2009-09-10
> **Emanuele_Z said:**
> Hi, I have to design a GUI for an application (C++).
Now, I don't care about Windows ports (I'm developing in Linux naturally), but I would like to get the following:

- GTK like preferred (target Gnome enviornment)
- Ease of use as Java Swing

I'm using gtkmm at the moment, but the fact it uses pango for the labels/text and there's no real guide to it (or at least I haven't been able to find it yet...) is a bit depressing.

Naturally I don't want to use a plain C api, because I don't want to write 100 functions to deal with click/event blah blah, but I would like to inhert from virtual methods using, naturally, C++.

Is there any GUI api which has simplicity of Java Swing/AWT but is written in C++ against gtk?

What do you reccomend?

Cheers,

Consider Vala or Mono? I'm not aware of any replacement for GTKmm as far as C++ bindings to GTK+ go, but an alternative-but-similar language should offer more natural-feeling bindings

---

### Post by SledgeHammer_999 on 2009-09-10
> **Emanuele_Z said:**
> I'm using gtkmm at the moment, but the fact it uses pango for the labels/text and there's no real guide to it (or at least I haven't been able to find it yet...) is a bit depressing.

Have you read the tutorial on the site? ->[link](http://gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html)


Also what are you trying to do with the labels that pango doesn't let you to do it?

---

### Post by Colonel Kilkenny on 2009-09-10
Personally I would just choose Qt. IMHO, it seems that atm. it's superior choice and future of Qt looks even better. C++ and Qt is great combination.

---

### Post by Emanuele_Z on 2009-09-11
> **SledgeHammer_999 said:**
> Have you read the tutorial on the site? ->[link](http://gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html)


Also what are you trying to do with the labels that pango doesn't let you to do it?

Hi...
The tutorial is not that bad but the official documentation is plain doxygen without any example for each method.
I've developed a lot with win32 gui API, some MFC and Java Swing/AWT and one good thing are the examples.
It's a bit of a shame that gtkmm isn't ver complete on that side.

Regarding Pango I didn't like the idea to specify a string to describe the format of a label, very CPU consuming...but if this is the way to do it...

Anyway, I think I'll still stick a bit with gtkmm for the meantime, or I'll start writing my own (simple) C++ wrapper Java like against GTK+.

I had a look at wxWidgets and actually the idea to be forced to use macros to setup callbacks etc etc is a bit scary in 2009... At least I would expect a good/massive use of virtual methods but probably they prefer the macros for optimization issues...

Anyway, if you have more suggestions/guides to gtkmm please do post them!

Cheers,

---

### Post by Emanuele_Z on 2009-09-14
One update.

While gtkmm docs are really hideous, the mailing list is populated with nice people, which helped me and gave me hints, where to search.

Now, I can say I've got a good experience/exposure to c/c++ and different GUIs... gtkmm is not very good for the *novice* c++/gui developers, still once you get a little of practice is very RAD like.

Plus the fact you can decide how to manage the memory yourself is a big plus, compared to other gui.

If only they would expand the docs with a *Read Me First Hint Section*, those libraries would be maybe the best oss/cross platform GUIs.

Cheers,

---

### Post by SledgeHammer_999 on 2009-09-14
@Emanuele_Z
are you the guy that recently asked about the liststore and the treeview widget in the mailing list? If yes, then it is a small world! lol

---

### Post by Emanuele_Z on 2009-09-14
Hell yes! :-)
Btw, I figured how to set the placement of some Widget(s) inside containers...
You have to use the methos inherted by Gtk::Misc, the *set_alignment()* or the similar *property_xalign()*...
To be honest wasn't so straightforward but still now I can do that.

Again, too bad the docs aren't *so* intuitive...
But the library itself is really good.

Cheers,

---

