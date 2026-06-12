---
title: "Anjuta doesn't have glade"
date: 2009-12-06
forum: Programming Talk
---

### Post by Johann-1.0 on 2009-12-06
Hello guys. I opened this thread because i was looking for an ide with gui builder integrated and find that apparently anjuta would work for me. I downloaded it from synaptics and found that the gui builder (glade) does not appear in anjuta. I read the tutorial in [www.anjuta.org](www.anjuta.org) (i think thats the url) and it says anjuta has glade incorporated...but when I look for it inside anjuta, i don't find anything. I think Anjuta is an excellent tool for me, because it can make software for C, C++, Java an Python...but i can't design gui's with it. Can you tell me how can I activate glade inside Anjuta?
Also, I was learning to program in Windows and there is Visual Studio, that is really perfect for the Win world...but is there a tool similar to Visual Studio in the Linux World? Specifically the Ubuntu World? As easy to use as Visual Studio?
I'd prefer GPL suggestions, rather than freeware or anything. Thank you.
I'm using Ubuntu 8.04 LTS.

---

### Post by IllegalCharacter on 2009-12-06
I have no idea if there is something like Visual Studio for Linux, I know a lot of Linux users just go with vim or emacs - I myself switched from Visual Studio to vim.
Anyway you can try just running glade outside of anjuta, you don't need to have them integrated. Glade will just spit out a layout file, which you can then load from your program.

---

### Post by 80aless on 2010-01-07
I also have the same problem: how to start glade in anjuta??
here [http://library.gnome.org/devel/anjuta-manual/stable/id2427721.html.en](http://library.gnome.org/devel/anjuta-manual/stable/id2427721.html.en)
there are the instructions, but they do not work for me (I have to open preferences, but where is it?=

---

### Post by matthew.ball on 2010-01-07
It's a Linux (perhaps just GNOME?) convention that application Preferences appear in the Edit menu.

For me right now, to view the Glade plug-in for Anjuta, create a new Glade file.

I've been playing around with gtk/wxWidgets quite a bit recently. I actually gave up using Glade to just use wxWidgets. There are a few wxWidgets form builders (wxFormBuilder, wxGlade), I didn't like the wxGlade interface, and wxFormBuilder wasn't consistent enough, so I have ended up just using emacs.

I would use Anjuta, even for the wxWidgets stuff, but it appears to create massively complex projects for some reason - sure I'll probably need it someday, but at the moment, a simple Makefile will suffice.

---

### Post by not_a_phd on 2010-01-08
I am a spoiled windows Borland C++Builder user that has been watching the evolving state of IDE's in the Linux environment for about 5-years now. During this time, I have tried building GUI's with the GTK, QT, and wxWidgets frameworks. Until about a year ago, I had only been successful building rudimentary apps using gcc + gedit. This was unacceptably tedious for rapid application development.

The first 'ray of light' for me occurred when the QT folks developed an Eclipse plug-in for their qt-designer. But, qtcreator sealed the deal for me. 

When I develop a GUI, I need an IDE that lets me graphically place widgets on a form or dialog, and then autocreate event handler stubs when I click on the widget in the design environment. (Like I said before, I am spoiled. This technology is possible; therefore, I need it.) 

I may be wrong, but it seems that qtcreator is the first IDE in linux (aside from the now defunct kylix) that pulls together in one app, the creation of the GUI design, and the autocreation of the software stubs for handling the events.

---

