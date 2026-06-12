---
title: "Restoring deleted menue item"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Bipod on 2008-07-22
Hi 
After an attempt to get a chat ocx running with Firefox in Wine I decided to find another way so I did an uninstall.
When I checked the main menu wine was still showing so I deleted the menu item..

Later on I tried reinstalling Wine to use with another application but the program now wont show up in the main menu 

I tried to use the Menu editor and Type in Wine when it asks me what Item to add and it shows me an icon I can use..
when the icon appears on the menu though it doesn't take me to the Wine folders.
What is the easiest way to restore this and get it all back on the main menu?

Thanx for any assistance with this

---

### Post by pauper on 2008-07-23
Here is an example if you want to create a path to program:

Applications--Wine--Programs--TVants--TVantsX.X.X.XX

Open "Main Menu". Click on "Application" under "Menus" window, select
"New Menu". Name it "Wine", fill out "Comments" if want to see tooltip with
some description. Now click on "Wine" under "Menus" window, select "New Menu"...
Repeat all these steps till you get to the shortcut to the program, i.e.
when TVants directory is created you will choose "New Item" for TVantsX.X.X.XX.

> ...it doesn't take me to the Wine folders.

Some useful entries under Applications--Wine

Name: Browse C:\ Drive
Command: xdg-open ~/.wine/drive_c

Name: Configure Wine
Command: winecfg

Name: Uninstall Software
Command: uninstaller

Name: Wine File Manager
Command: winefile


P.S. See [this thread](http://ubuntuforums.org/showthread.php?t=59514) if you have trouble removing entries after
uninstalling wine programs.

Some residual files/directories could be find here:

$HOME/.local/share/applications/wine/Programs
$HOME/.local/share/icons
$HOME/.local/share/desktop-directories
$HOME/.wine/drive_c/windows/temp

All files deleted in winefile end up here:

$HOME/.local/share/Trash

---

