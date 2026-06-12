---
title: "Suggestions on IDE for C++ and GTK+"
date: 2010-10-18
forum: Programming Talk
---

### Post by samalex on 2010-10-18
Hey guys --

I've been around the block with coding for years and know enough C++ to get a side project going, but the last real IDE I used for C++ was Borland C++ 3.5 for DOS :) 

I use NetBeans for PHP codeing so I'm thinking of picking it up as my IDE of choice for C++, but is it possible to bundle GTK+ into it somehow?  Just curious...  If not can you guys recommend an alternative?  I've heard good things about Enveria so I might check it out as well.

Also I'm not opposed to using NetBeans for the coding then some other IDE for the GTK+ interface, but it'd be nice to have it all in one place.

Take care --

Sam

---

### Post by Simian Man on 2010-10-18
> **samalex said:**
> I use NetBeans for PHP codeing so I'm thinking of picking it up as my IDE of choice for C++, but is it possible to bundle GTK+ into it somehow?
If you're asking if NetBeans can compile and link C++ programs with GTK+, then yes.  If you're asking if it gives you a form editor for creating a GTK+ GUI, then no.  Glade is one option for creating the GUI, but there is no decent all in one solution I know of.

If you're really open to suggestions, I'd recommend ditching C++ (which is a horrible language for GUI programming), and using C# with Monodevelop - which includes a GUI designer.  You'll be way more productive even while learning a new language :).

---

### Post by SledgeHammer_999 on 2010-10-18
I suggest not to use Gtk+ and C++ directly. I suggest using Gtk's C++ bindings called [Gtkmm](www.gtkmm.org). Of course if you REALLY want it, you could directly use the C API.

---

### Post by samalex on 2010-10-18
Thanks for the suggestions.  I have played with MonoDevelop and I like it, especially given we use C# on Visual Studio 2008/2010 at work.  It just seems there's lots of hype behind C++ and GTK+ which is why I figured that combination was the 'norm' for most, but I'm game to branch out.  I've also created a few 'hello world' apps in Qt, so I might check that out more as well.

Also why is C++ horrible for GUI?  Is it too nuts and bolts?  Seems most of the other languages/frameworks have more GUI libraries than C++ so is that why?  Just curious.

Take care ..

---

