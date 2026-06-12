---
title: "how to install and run GTK+???"
date: 2008-08-29
forum: Programming Talk
---

### Post by ra2008 on 2008-08-29
Hi,
i am using Ubuntu8.04.
i started up to install GTK+. By reading the guide in its website, i found in synaptics that all packages, dependencies, and libraries are already installed on my PC.

1. so, is there sthg more i have to install to get it run? if yes what it ??

2. what is the command to run GTK+? 

3. When GTK+ runs, it opens in an IDE or i have to install Ajunta to be the IDE for GTK+?

thanks

---

### Post by kknd on 2008-08-29
GTK is a library for GUI. It doesn't comes with special text editors.

Follow the tutorial at
[http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)

---

### Post by samjh on 2008-08-30
> **ra2008 said:**
> i started up to install GTK+. By reading the guide in its website, i found in synaptics that all packages, dependencies, and libraries are already installed on my PC.

1. so, is there sthg more i have to install to get it run? if yes what it ??

2. what is the command to run GTK+? 

3. When GTK+ runs, it opens in an IDE or i have to install Ajunta to be the IDE for GTK+?

thanks
[list=1][*]To run GTK+ apps, you'll have everything you already need if you are using Ubuntu or Xubuntu.  If you want to program GTK+ applications, you'll need the development packages as well.  Development packages have "-dev" suffix.
[*]You don't "run" GTK+.  It's a library that programs use to display graphical user interfaces.
[*]If you're talking about programming software that uses GTK+, you don't need any special IDEs.  To compile using the command-line and the gcc compiler, you just need to append `pkg-config --cflags --libs gtk+-2.0` to the gcc command. Example: **gcc myprogram -o myprogram.c `pkg-config --cflags --libs gtk+-2.0`**[/list]

---

### Post by ra2008 on 2008-08-30
hi, thanks for the replies.
i am asking that Q3, coz i found that in KDE (KDevelop) there is a built in IDE . does this mean KDE is more user friendly and easier to work with?
i am a newbie in GUI programming. so which one do u recommend either working with C++ or C???
thanks

---

### Post by techmarks on 2008-08-30
If you decide to use QT on KDE then you'll have to
code in C++.

I recently had this sort of question before me.

I'm working on a graphics program that uses OpenGL, and decided to use GTK+ for the GUI part.

I thought I'd write it in C since GTK+ is C (I am aware that you can use GTK+ with C++ thru gtkmm or even without gtkmm)

Everything was going well and I had a GTK window to render OpenGL in (using Gtkglext)

Now I needed a math expression parsing library, and the best ones I found were written in C++.

No problem I thought I'll just compile the program to C++.

Normally all C code will upgrade to C++ (you can't go the other way without more problems)

When I compiled my C program as C++ I got some errors (which I expected) and a few minor C issues fixed right away.

However now I'm getting syntax errors from Gtkglext!

The beauty of GTK is that GTK itself can be compiled as C or C++
without any problem at all, but I can't say the same of Gtkglext.

Sure I can go into the Gtkglext code and start fixing these problems, (which I'm sure can be done) but now everything will take me more time.

So anyway as I don't wish to write a math expression parser (what for? it's been done, why spend more time on it)
So now I'm going with C++ after all, and can't use GTK+ because I don't want to spend time re-writing the gtkglext parts.

So I've decided to use Fltk (it's C++ GUI library and makes OpenGL rendering super easy), I would have preferred Gtk but...

now then should you use C or C++?
My point is it just depends on what your specific program needs to do and what libraries if any you need.

Either C or C++ or maybe some other language could be best.

---

### Post by samjh on 2008-08-30
> **ra2008 said:**
> hi, thanks for the replies.
i am asking that Q3, coz i found that in KDE (KDevelop) there is a built in IDE . does this mean KDE is more user friendly and easier to work with?
i am a newbie in GUI programming. so which one do u recommend either working with C++ or C???
thanks

No, it doesn't mean that KDE is more friendly to work with.  KDE's "official" IDE is KDevelop.  But it is not built-in; you have to install it separately in most Linux distros.

Gnome's "official" IDE is Anjuta, but I've read some bad reviews about it, especially when sharing code around with others.  I personally had no major problems with it.

Now some questions for you, so that we can give better advice...

Do you have to work with C or C++?  Are you at least familiar with those languages?  GUI programming is not for people who are new to a language.

If you are new to programming, I'd strongly recommend you learn to program first.  If you want to program GUIs as quickly as possible, try learning Python and its Tkinter library, or use Python and PyGTK (Python's GTK+ binding).

If you are familiar with C or C++, then either GTK+ or Qt will do the job for you as far as GUI is concerned.  With GTK+, you can use C++ by using GTKmm (GTK+'s C++ binding).

Personally I use C++ with Qt, because Qt is very well documented, popular with developers both commercially and in the FOSS community, and Qt includes several other very useful libraries aside from the GUI library.

---

### Post by ra2008 on 2008-08-30
hi,,
actually i want to make a Graphical interface to read/write from hardware like serial port or parallel port. (simple data acquisition software).
so what do u recommend for that? KDE or GTK+?? C or C++??
thanks

---

### Post by samjh on 2008-08-30
> **ra2008 said:**
> hi,,
actually i want to make a Graphical interface to read/write from hardware like serial port or parallel port. (simple data acquisition software).
so what do u recommend for that? KDE or GTK+?? C or C++??
thanks
Again, either one will do.

But since you'll find more libraries for low-level I/O written in C than C++, perhaps C and GTK+ would be the way to go.  You can use Glade to design GTK+ GUIs in WYSIWYG fashion so you don't have to code it by hand.

---

### Post by nvteighen on 2008-08-30
> **ra2008 said:**
> hi,,
actually i want to make a Graphical interface to read/write from hardware like serial port or parallel port. (simple data acquisition software).
so what do u recommend for that? KDE or GTK+?? C or C++??
thanks

I smell some problems here.

1) there's no KDE GUI library, like there's no GNOME GUI library. GNOME is a bunch of interconnected programs that have a coherent look-and-feel because using the same GUI library called GTK+ (which by accident happens to be written by the same people from GNOME) and KDE is the same, but of programs using a library called Qt (which is not written by the KDE team). The Xfce desktop also bases itself on GTK+, but has no relationship with GNOME.

But you can use GTK+ programs in KDE and Qt programs in GNOME. You can even use Qt programs in Windows if compiled for that platform (Skype, for example)... In other words, if you have the library installed, you can use it no matter what desktop environment you use.

2) When programming, you should separate interface from implementation. In other works, you have to make your read/write port functions work for any interface you choose afterwards, so questions like "GTK+ or Qt or command-line?" doesn't stop your project.

Create the interface separatedly: it just has to be a way to allow the user call the implementation's functions. Keep in mind that a command-line is also an interface, so you may test your program with that first and then replace it by a graphical one.

So, the choice of the GUI toolkit should be irrelevant for your ports reading/writing program.

Remember: The implementation is the master; the interface, the slave.

---

### Post by jespdj on 2008-08-30
> **nvteighen said:**
> ... You can even use Qt programs in Windows if compiled for that platform (Skype, for example)... In other words, if you have the library installed, you can use it no matter what desktop environment you use.
Skype for Windows is not a Qt program; it uses the Win32 API which is native on Windows. (The Linux version of Skype was written much later than the Windows version).

You can also run GTK+ programs on Windows (they have to be recompiled though if they're written in C or C++); GTK+ is also available for Windows.

---

