---
title: "added a program to wine directroy but not showing up"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by stinger30au on 2008-07-27
i have a small app that runs fine in wine but has no installer.
so i just copied it to the wine directory hoping that it would be automatically be added to "programs" but his is not the case

how do i add the program in somehow so when i click on
applications->wine->programs

my app will show up???

thanks

---

### Post by rockerphil on 2008-07-27
if the program works fine in wine and you don't want to use the terminal to run "wine <file.exe>" then i'd just put the .exe file to the program on the desktop, it'll be right there for you to double click whenever you please

---

### Post by ajmorris on 2008-07-27
> **stinger30au said:**
> i have a small app that runs fine in wine but has no installer.
so i just copied it to the wine directory hoping that it would be automatically be added to "programs" but his is not the case

how do i add the program in somehow so when i click on
applications->wine->programs

my app will show up???

thanks

hi there,
you can create a .desktop file in /usr/share/applications the menu will automatically pick this up. Just model one of the other .desktop files in there for yours.

[quote=rockerphil]if the program works fine in wine and you don't want to use the terminal to run "wine <file.exe>" then i'd just put the .exe file to the program on the desktop, it'll be right there for you to double click whenever you please[/quote]

If you do this, it would not run, you would have to create a link to the .exe file, i.e. a symbolic link via the ln -s command in the terminal.

AJ

---

