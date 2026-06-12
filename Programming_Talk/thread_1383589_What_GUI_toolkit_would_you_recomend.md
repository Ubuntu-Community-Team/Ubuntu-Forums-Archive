---
title: "What GUI toolkit would you recomend?"
date: 2010-01-17
forum: Programming Talk
---

### Post by SIGTERMer on 2010-01-17
I'm new to GUI programming in Linux (though i had done a few projects with Java's swing in the past), and am hoping for some suggestions regarding what libraries to use with C.
I originally had my eyes on wxWidgets but it seems that there are no C bindings available. so I'm currently investigating gtk.
The main feature I need available in the libraries is that they play nice with C. Cross-platform comes in second.

Are there other alternatives I should be aware of? any tip or suggestion is appreciated.

Thanks

---

### Post by phrostbyte on 2010-01-17
GTK+ is the archtypical C GUI toolkit. Motif would be another option, but it's rarely used.

---

### Post by hoppipolla on 2010-01-17
I would say Qt but apparently it's C++ :(

---

### Post by WitchCraft on 2010-01-17
C++ is a superset of C, so why not using it ?
As long as you don't programm on the kernel itself, you don't need C.

If what your application has to do is not time-critical, then I'd even use a higher level language, like Python + wxWidgets, or C# with mono.

---

### Post by MadMan2k on 2010-01-17
you can perfectly continue programming Swing using Java on Linux. There is a native Look and Feel for it, which does not look too bad. (at least not worse than wxWidgets)
You can also take a look at SWT...

---

### Post by Sinkingships7 on 2010-01-17
GTK+ for Gnome, and Qt for KDE. It's really as simple as that. If you're set on using C, GTK+ is what you want. C++ for Qt. Both are cross-platform. From what I've heard, Qt has a very clean, useful API.

---

### Post by not_a_phd on 2010-01-17
> **Sinkingships7 said:**
> GTK+ for Gnome, and Qt for KDE. It's really as simple as that. If you're set on using C, GTK+ is what you want. C++ for Qt. Both are cross-platform. From what I've heard, Qt has a very clean, useful API.

One thing I would add is that at my last look Qt has a more developed IDE for designing interfaces and putting together applications. This is an enormous help for someone coming up the learning curve on a new framework. I know Gtk has Glade. But this is interface only. Leaving the developer to hand hack the main and event stubs. I personally never was able to get Anjuta to work.

---

### Post by SIGTERMer on 2010-01-21
Thanks everyone.

based on your inputs, it seems that gtk is my best choice at this stage.

WitchCraft: I work in an environment where C is far more prevalent than C++. it would be very inconvenient for me to use two different programming paradigms for one project. besides, I like the way how C does things ;)

---

### Post by hessiess on 2010-01-21
> **SIGTERMer said:**
> WitchCraft: I work in an environment where C is far more prevalent than C++. it would be very inconvenient for me to use two different programming paradigms for one project. besides, I like the way how C does things ;)

GTK+ is object oriented using GObject, mixing OOP and procedural programming is inevitable because OOP lends itself nicely to the implementation of GUI tool kits.

---

### Post by SIGTERMer on 2010-01-21
> **hessiess said:**
> GTK+ is object oriented using GObject, mixing OOP and procedural programming is inevitable because OOP lends itself nicely to the implementation of GUI tool kits.

I know, but the OOP aspect of it is implemented in C and not C++. and until I'm forced to use C++ (that day is approaching fast), I think I'll stick with what I know best. I'm just that lazy...

---

