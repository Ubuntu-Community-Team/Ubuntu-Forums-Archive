---
title: "Major Cross Platform Softwares on Ubuntu"
date: 2017-07-19
forum: New to Ubuntu
---

### Post by rajdeeproy on 2017-07-19
Hello Everyone, 
I am a newbie here. Just registered. I would appreciate your suggestions about the software(s)
which can be run on cross platforms parallelly with Windows here in Ubuntu.
TIA
):P

---

### Post by mrgnome on 2017-07-19
There's some great stuff on offer. LibreOffice for an office suite. Google Chrome or Mozilla Firefox are both great cross-platform browser options, and if you need an email client, Thunderbird is amazing (as long as you can stand the interface). Pigdin is a good chat client, and for virtualization, VirtualBox is hard to beat. Let me/us know if you need something else :)

**EDIT: **Make sure you don't use anything from the GNOME/KDE Projects, because they're Linux-only.

---

### Post by vasa1 on 2017-07-19
> **rajdeeproy said:**
> Hello Everyone, 
I am a newbie here. Just registered. I would appreciate your suggestions about the software(s)
which can be run on cross platforms parallelly with Windows here in Ubuntu.
...
Your question is too broad. You can, with a minimum amount of internet searching, probably answer such a question yourself.

---

### Post by vocx on 2017-07-19
> **mrgnome said:**
> There's some great stuff on offer. LibreOffice for an office suite. Google Chrome or Mozilla Firefox are both great cross-platform browser options, and if you need an email client, Thunderbird is amazing (as long as you can stand the interface). Pigdin is a good chat client, and for virtualization, VirtualBox is hard to beat. Let me/us know if you need something else :)

**EDIT: **Make sure you don't use anything from the **GNOME/KDE Projects, because they're Linux-only**.

You are mistaken when you say GNOME/KDE are Linux-only.

Gnome and KDE are encompassing projects that feature many programs. Those programs are built around the GTK+ and Qt libraries, respectively, which provide graphical interfaces and other functionality like internationalization support. As a matter of fact GTK+ and Qt are cross-platform and can be compiled for different systems. As long as GTK+ and Qt can be installed in Windows, the programs using those libraries will be able to be compiled and run in Windows. This is the case for Geany (text editor), GIMP (drawing and photo editing), GVim (interface to vim, text editor), Octave (numerical computation), Kate, Kile (text editor), and many others. In Linux it is trivial to install GTK+ and Qt programs because the libraries are already there for use for the entire system. In Windows, the libraries have to be installed, so what programs like Geany and GIMP do, is they include their personal copy of the GTK+ libraries with them. In this way they avoid relying on system-wide libraries, but at the same time they use a bit more space on your hard drive. It's like a restaurant. In Ubuntu, you go to a restaurant and you just order your food and eat it with the cutlery you are given. In Windows, you have to bring your own cutlery, ceramic plates, and glasses, but you can still have the meal there (you can still install the program but you have to bring the dependencies yourself).

Some people have developed an installable KDE package which includes the Qt libraries, and many programs that rely on them. [https://kde-windows-installer.en.uptodown.com/windows](https://kde-windows-installer.en.uptodown.com/windows) [https://chocolatey.org/about](https://chocolatey.org/about) [https://chocolatey.org/profiles/KDE](https://chocolatey.org/profiles/KDE)

It is always recommended to look at a particular program's website to look for a Windows version. As GTK+ and Qt are cross-platform, many programs that use these libraries can make their program run in Windows.

There is also Cygwin. Cygwin provides the core components of a Linux system, like the terminal (bash), and many command line utilities (ls, cd, mkdir, etc.), plus system libraries (C library, X windows, etc.), and compilers (gcc, g++), all native to Windows. In this way, it is possible to have the terminal and do many things you can do in Linux, but natively in Windows. [https://www.cygwin.com/](https://www.cygwin.com/)

Using Cygwin it is also possible to recompile the GTK+ and Qt libraries for Windows (for advance users only), and in this way install many programs for these libraries.

---

