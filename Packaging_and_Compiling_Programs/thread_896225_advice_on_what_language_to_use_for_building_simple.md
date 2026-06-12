---
title: "advice on what language to use for building simple GUI in windows"
date: 2008-08-21
forum: Packaging and Compiling Programs
---

### Post by syxbit on 2008-08-21
yea, I know, I'm asking for windows, but hear me out.
I (personally) only use linux, but my job requires windows.
they want me to write a simple gui that can accept and pass text from a file.
I'd like to use a 'linux' language (by that I mean a language that is commonly used in linux, like python).

I've coded here and there in C, Java, and some assembly, and my Boss wants me to use Visual Studio to do it (which i'd have to learn)
so i figure, why not learn a language that could do the job and would be useful when i get my dream job doing linux stuff.

so, it needs to be a language that works easily in windows and makes GUI stuff easy.
any ideas?

---

### Post by lucho64 on 2008-08-21
Why don't you use C++ and gtkmm? or C and Gtk+? Gtk, of course, is the widget tool kit used by gnome, and it so happens that it integrates nicely with VisualStudio. As a bonus, if you are a bit careful, your programs will be portable across platforms. Of course Gtk has bindings for python and all other major languages, but I don't think VisualStudio would know about it :)

---

### Post by ggaaron on 2008-08-21
Qt is portable, if you are careful not to use platform specific libraries your application should run on more platforms. If you are making proprietary software you will have to pay for it though, also I think that it integrates with Visual Studio.

---

### Post by mujambee on 2008-08-22
If forced to use VisualStudio, you'll have to stick to C, C++, C#, VB or Java. As you have some previous experience with C and Java we can rule out C# and VB. This leaves three approaches:

1. Use C++ with MFC. MFC will give you a simple, functional GUI interface in no time, but if you try to do something a bit more complex it can be a real pain. Good for very simple GUI.

2. Use C with API. It may be a bit more difficult to get rolling, but when you grasp the concept it is easy to gain speed.

3. Use Java. This way you won't learn anything specific to Windows, so all your learning will be portable. Can't advice much on this, I've used it only marginally and never took to like it.

However, if you give us a bit more detail on what you need to do I may be of more help.

[I]Edit:

GTK+, Qt and such would need to istall the runtimes on every machine you will run your app, something most IT departments will not even think about; that would make the native APIs your only choice.

Also, bear in mind that you won't learn the windows API in a couple of hours...

[/I]

---

