---
title: "RAD with Glade??"
date: 2007-01-24
forum: Programming Talk
---

### Post by rekahsoft on 2007-01-24
hi all, i am just wondering if using glade is a valid replacement of developing the GUI myself. Is there any performance issues. Is libglade slow at loading the generated xml files from glade? Is it possable to make highly customizable interface or is it just for quick jobs? What are the pro's and cons?
I have not yet learned gtk+, gtkmm, or pygtk but will get to learning them ASAP after i know the languages better (i am not totally proficient at C, C++ or python [I have been learning them all at the same time]). I have in the past (with java) preferred to hand-code the interface but since NetBeans and its awesome GUI builder (matisse) i have began to slack off. But in that case i know what is happening so i can easily debug problems, so before i do anything with GTK+ (and its wrappers/bindings/interfaces) i will learn to hand code the GUI. Anyways, thanks for the help :)

---

### Post by runningwithscissors on 2007-01-24
> **rekahsoft said:**
> hi all, i am just wondering if using glade is a valid replacement of developing the GUI myself.
Yes.
> Is there any performance issues. Is libglade slow at loading the generated xml files from glade?
No.
> Is it possable to make highly customizable interface or is it just for quick jobs? What are the pro's and cons?
It is possible to make complicated interfaces. Heck, it is there so that you can make complicated interfaces
> I have not yet learned gtk+, gtkmm, or pygtk but will get to learning them ASAP after i know the languages better (i am not totally proficient at C, C++ or python [I have been learning them all at the same time]).
Glade genrates C code. GTK+ is written in C. For the sake of consistency, go with C. It is not particularly difficult to learn if you've had prior programming experience.
>  I have in the past (with java) preferred to hand-code the interface but since NetBeans and its awesome GUI builder (matisse) i have began to slack off. But in that case i know what is happening so i can easily debug problems, so before i do anything with GTK+ (and its wrappers/bindings/interfaces) i will learn to hand code the GUI.
I hand code the GUI for my small apps using GTK+. It is quite simple, but Glade is definitely the much quicker option.

---

### Post by rekahsoft on 2007-01-24
Isn't generation C code depreciated for the newest version of glade? Now doesn't it just generate the .xml file and you use libglade to load it?

EDIT: This is from the glade site:
**One of the main differences from glade-2 is that C code generation has been removed from glade-3: this has been done on purpose, since using generated code is deprecated; the preferred way to use glade files is with libglade (if code generation is needed, this can be provided as another tool or plugin, code generation is simply not a part of the glade-3 project).**

---

### Post by runningwithscissors on 2007-01-24
> **rekahsoft said:**
> Isn't generation C code depreciated for the newest version of glade? Now doesn't it just generate the .xml file and you use libglade to load it?

EDIT: This is from the glade site:
**One of the main differences from glade-2 is that C code generation has been removed from glade-3: this has been done on purpose, since using generated code is deprecated; the preferred way to use glade files is with libglade (if code generation is needed, this can be provided as another tool or plugin, code generation is simply not a part of the glade-3 project).**
Ah. Haven't used it in a while, so wan't aware of that development.
Thanks for the info.

---

### Post by rekahsoft on 2007-01-24
> **runningwithscissors said:**
> Ah. Haven't used it in a while, so wan't aware of that development.
Thanks for the info.

no prob :)

---

### Post by lnostdal on 2007-01-25
...just adding to what has already been said and confirm that Glade and its surrounding tools/libraries, support and documentation is mostly excellent for GUI-work. :)

---

### Post by rekahsoft on 2007-01-25
> **lnostdal said:**
> ...just adding to what has already been said and confirm that Glade and its surrounding tools/libraries, support and documentation is mostly excellent for GUI-work. :)

ok, i will lean to use glade and hand code GTK+ in sync. :) Thanks for the help

---

### Post by MadMan2k on 2007-01-25
you said you know java?
[http://java-gnome.sourceforge.net/4.0/doc/api/org/gnome/glade/Glade.html](http://java-gnome.sourceforge.net/4.0/doc/api/org/gnome/glade/Glade.html)

---

