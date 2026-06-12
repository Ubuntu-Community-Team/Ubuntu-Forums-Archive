---
title: "GTK+..how about windows and mac?"
date: 2011-08-30
forum: Programming Talk
---

### Post by nickos on 2011-08-30
My question is :

will a gtk+ app for ubuntu/gnome be able to run on windows and mac?how is it?will be provide the graphics and environment for windows and mac(i mean the blue colored windows and right buttons for windows and grey style window for mac and stuff) or will i have to write it using windows/mac GUI?

---

### Post by SledgeHammer_999 on 2011-08-30
It is supposed to work for Windows/Mac too. (you need to recompile your program though). They even provide an installer for it here: [http://www.gtk.org/download/index.php](http://www.gtk.org/download/index.php)

And yes it should draw the correct windows/buttons/widgets in the native styles/colors.

Never tried to compile something though on windows.

---

### Post by ajgreeny on 2011-08-30
Gimp is a good example of a gtk application that will run on windows but to install and use it you have to use a specific installer which includes the gtk requirements.

See [http://sourceforge.net/projects/gimp-win/files/](http://sourceforge.net/projects/gimp-win/files/)

---

### Post by JupiterV2 on 2011-08-31
You may also want to look at Pidgin or my own program (see the link in my sig) to see another way of installing a GTK+ program on Windows. There are certain challenges to be aware of but it's not actually that hard. I've not attempted to build on MacOS, yet. The only real challenge is providing a Windows version of GTK+ with your program since most Windows machines won't already have it installed. The three ways most people seem to resolve the issue are:

1) Require the user to install GTK+ separately themselves (trivial but I question whether most Windows users will be willing to do this).
2) Bundle a GTK+ Windows installer with your program and automatically run it as part of the install process (a very common technique in the Windows world). - GIMP, gedit (I think)
3) Bundle the GTK+ Windows runtimes in your program and install them into a private directory if a system-wide version of GTK+ is not already installed (usually a sub-directory of your application). - Pidgin, Vocab Builder

---

### Post by forrestcupp on 2011-08-31
Hopefully it's changed since I used it, but a few years ago, I ported a GTK+ program to Windows. It didn't seem quite as native as wxWidgets. I don't know if it's still like it was, but it used to not use native Windows controls. You had to specifically tell it to emulate Windows controls with a theme.

I liked wxWidgets a little better because it actually uses the native Windows or GTK controls depending on the platform it's running on.

---

### Post by JupiterV2 on 2011-09-01
> **forrestcupp said:**
> Hopefully it's changed since I used it, but a few years ago, I ported a GTK+ program to Windows. It didn't seem quite as native as wxWidgets. I don't know if it's still like it was, but it used to not use native Windows controls. You had to specifically tell it to emulate Windows controls with a theme.

I liked wxWidgets a little better because it actually uses the native Windows or GTK controls depending on the platform it's running on.

It hasn't changed.

---

