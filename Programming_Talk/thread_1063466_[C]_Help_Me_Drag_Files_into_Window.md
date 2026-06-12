---
title: "[C] Help Me Drag Files into Window"
date: 2009-02-07
forum: Programming Talk
---

### Post by loganwm on 2009-02-07
I'm currently working with SDL in C on a project and I'm attempting to Drag files into the program's window and the program detect them and preform an operation (such as load them).

I believe I've heard it referred to as OLE? But then again, I might just be out of my mind.

For example, I'm trying to drag a JPEG into my window and then load it into the program.

---

### Post by eye208 on 2009-02-07
> **loganwm said:**
> I'm currently working with SDL in C on a project and I'm attempting to Drag files into the program's window and the program detect them and preform an operation (such as load them).
Drag & drop events between applications are handled by the GUI toolkit (GTK+ or Qt), not SDL. If you are familiar with Windows, you can see SDL as a counterpart to DirectX, and GTK+/Qt as a counterpart to MFC.

Here's a reference page about drag & drop in GTK+:

[http://library.gnome.org/devel/gtk/stable/gtk-Drag-and-Drop.html](http://library.gnome.org/devel/gtk/stable/gtk-Drag-and-Drop.html)

---

### Post by loganwm on 2009-02-08
> **eye208 said:**
> Drag & drop events between applications are handled by the GUI toolkit (GTK+ or Qt), not SDL. If you are familiar with Windows, you can see SDL as a counterpart to DirectX, and GTK+/Qt as a counterpart to MFC.

Here's a reference page about drag & drop in GTK+:

[http://library.gnome.org/devel/gtk/stable/gtk-Drag-and-Drop.html](http://library.gnome.org/devel/gtk/stable/gtk-Drag-and-Drop.html)

I'm well aware that the major toolkits provide this. I'm attempting to avoid the major windowing toolkits if there's another library that may handle it?

If not it's alright, I'd just like to know as many options as possible before I design my programming around a solution.

Thank you for your suggestion.

---

### Post by eye208 on 2009-02-08
> **loganwm said:**
> I'm well aware that the major toolkits provide this. I'm attempting to avoid the major windowing toolkits if there's another library that may handle it?
Detecting the drag & drop action may well be possible using SDL alone, but I think you need the windowing toolkit anyway to access the meta information associated with the action (i.e. which file icon was dropped on the window) because this information doesn't exist at the SDL level.

---

### Post by slavik on 2009-02-08
the first thing I would try is to print all SDL events that come in through your mainloop, then see if it even catches the drag and drop, otherwise, ask SDL devs ...

---

### Post by CptPicard on 2009-02-08
Considering where this project is going (the infamous "Stacks" :) ), you certainly need GUI toolkit integration, because you need file thumbnail previews and most probably also KParts/DCOP-style integration of applications. Alternatively you need to be reimplementing everything from scratch, and writing what sounds like essentially as new window manager plus application platform (à la KDE) is no small feat, and even if you could do this, everyone else would just have to start recoding their apps against your APIs.

---

### Post by loganwm on 2009-02-08
> **CptPicard said:**
> Considering where this project is going (the infamous "Stacks" :) ), you certainly need GUI toolkit integration, because you need file thumbnail previews and most probably also KParts/DCOP-style integration of applications. Alternatively you need to be reimplementing everything from scratch, and writing what sounds like essentially as new window manager plus application platform (à la KDE) is no small feat, and even if you could do this, everyone else would just have to start recoding their apps against your APIs.

It's not Stacks, its really just a simple viewer for photos and some other things I'd like to incorporate. I'm not trying to reinvent the wheel.

---

### Post by CptPicard on 2009-02-08
> **loganwm said:**
> It's not Stacks, its really just a simple viewer for photos and some other things I'd like to incorporate. I'm not trying to reinvent the wheel.

Well, if it's simple it is even more reason to use existing parts of the wheel...

---

### Post by loganwm on 2009-02-08
> **CptPicard said:**
> Well, if it's simple it is even more reason to use existing parts of the wheel...

I'm not trying to be rude, I'm just saying, I'd like as small and simple of a memory footprint as possible, but I appreciate the help?

---

### Post by CptPicard on 2009-02-08
I am not trying to be rude either, but if you have got a windowing environment running already, *not* making use of it just increases whatever footprints you're producing if the application pulls in unnecessary dependencies...

---

### Post by Tomosaur on 2009-02-08
> **loganwm said:**
> I'm not trying to be rude, I'm just saying, I'd like as small and simple of a memory footprint as possible, but I appreciate the help?

The window manager will already be running - the only 'extra' stuff being used is anything whatever your app requires to run.

---

