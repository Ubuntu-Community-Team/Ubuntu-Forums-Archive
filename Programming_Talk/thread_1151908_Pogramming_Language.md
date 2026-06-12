---
title: "Pogramming Language"
date: 2009-05-07
forum: Programming Talk
---

### Post by mike0liver on 2009-05-07
I've recently graduated from Windows XP and am finding Linux a far better OS than I expected. However, I want to produce a couple of free-standing applications related to my wargaming hobby and can't identify the best option.

I used to use Visual Basic 6 on Windows and would like to find something similar for Linux so I don't have to spend a load of time learning something new (lazy or what?). Can anyone point me in the right direction, please? It would be nice to have something with a downloadable manual that includes reserved words, syntax examples, etc.

I have tried installing and opening Python, but all I get is a Terminal window with a flashing cursor. I'm sure I must be missing something but, being new to Ubuntu & Linux, I have no idea what it might be.

Cheers,

Mike

---

### Post by simeon87 on 2009-05-07
Python would be a good choice. Try this tutorial for example to get you started with the interpreter (which is what you've seen): [http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

---

### Post by jespdj on 2009-05-07
Try C# with MonoDevelop. You can find a nice [set of tutorials on tuxradar.com](http://tuxradar.com/hca).

---

### Post by tribaal on 2009-05-07
You might want to install Glade (from the repositories).
This lets you design the user interface interactively, then you can ask it to export the gui (as a .glade file), and/or let it generate the GUI code for you.

Pretty similar to VB, except you need to use two separate editors (one for the GUI and one for the code itself).

This helped me design the small tools I coded for myself, too. 

Hope this helps!

- Trib'

_References:_
[One article]("http://www.linuxjournal.com/article/7421")
[Another]("http://www.pygtk.org/articles/pygtk-glade-gui/Creating_a_GUI_using_PyGTK_and_Glade.htm")

---

### Post by necrolin on 2009-05-07
Mono actually allows you to use both C# and VB.NET. Since you already stated that you're familiar with visual basic why don't you just continue to use that? Note that there's no GUI designer for winforms for Linux, but there is Mono Develop. Mono Develop is an IDE which works with Mono. It has a GUI designer which uses GTK widgets. There'd be some learning involved, but probably this would be the path of least resistance.

From what I've read about Mono, it would allow you to run your winforms programs.... you'd just have to design them in Windows. VirtualBox maybe? Work in VisualStudio and then run in Linux?

Just a few idea. Note that I'm not a mono developer so I'm not sure how well mono works but it sounds like it's worth a try.

---

### Post by mike0liver on 2009-05-07
Thanks. As I said, I've tried Python but it doesn't look or behave anything like VB, so it will mean a heavy learning process I don't really have time for. However, I won't condemn Python out of hand; I'll try a few other suggestions first.

Cheers,

Mike

---

### Post by mike0liver on 2009-05-07
Thank you. I'll check this one out later. I tried learning C by correspondence course a few years back and it hurt my brain but nothing will get ignored :-)

Cheers,

Mike

---

### Post by mike0liver on 2009-05-07
This sounds a good candidate. An initial tinker with the controls suggests I'm going to have to read the manual a bit more fully but it's an encouraging start. Thanks for the suggestion.

Cheers,

Mike

---

### Post by mike0liver on 2009-05-07
I run Wine on my machine and it seems to work pretty well with the Windows applications I've tried so far. I'll check out Mono and see what it offers. The suggestion is appreciated.

Cheers,

Mike

---

### Post by Marco A on 2009-05-07
.

---

### Post by kostkon on 2009-05-07
Check [*Gambas*]("http://gambas.sourceforge.net/").

Quoting from its site:
> Gambas  is a free development environment based on a Basic interpreter with object extensions, a bit like Visual Basic™ (but it is NOT  a clone !).

You can easily install it from the repos.

Hope that helps.

---

