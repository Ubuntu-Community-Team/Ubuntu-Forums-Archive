---
title: "Customize the application grid in Ubuntu 20.04"
date: 2020-05-14
forum: New to Ubuntu
---

### Post by magunto on 2020-05-14
Hi, 
I am new to gnome ubuntu desktop, and currently using ubuntu 20.04. I enjoy the desktop, but there are few things that bother me with the application grid (I don't know the precise name of this feature)

1. when openin the application grid, the applications are displayed very dense to each other (almost next to each other) in the center of the screen . The majority  of the screen is not used at all - is there a way to move them away to have better visibility and convienence?

2. I know there is a possibility to create folder in the application grid and group applications. But when the folder is at the first page, and I want to add an application that is on the last page I don't see a way to do it - when moving the application up to the border of the grid page, the page doesn't flip/scroll. Is there a way to make the page flip/scroll when moving application up or down?

3. There are few applications that (for whatever reason) are duplicated in the grid. They have similar icons, and their name start same way, but they have different endings in description, which I can see when typing their name. But on the grid view the description under icons is too short and I don't see the full name (with ending which differentiate them), even when I hover the mouse pointe over them. - Is there a way to change it - make the description longer or make it appear in full when hovering a mouse over the icon?

Thanks!

---

### Post by vanadium on 2020-05-14
Just some thaughts

1) I am surprised to learn this. It would be good to post a screen shot. Typically, applications are in a wide grid covering 2/3 of the screen width, with plenty of space between them (many used to complain about the large empty spaces in Gnome Shell).

2) Strange again. For me, the pages flip when dragging the application to the bottom of the screen.

3) Applications on the grid are defined by application launchers. These are little text files with the extension .desktop. They live in /usr/share/applications (and in dedicated folders for snap applications) for system wide available applications. Each user also has a .local/share/applications folder, where launchers live that only appear in the user's menu. In addition, the launchers there may override the same launchers (same file name) living in the system wide folders.

You could use a terminal command to locate all .desktop folders corresponding with a duplicate entry you see:
> find / -name '*.desktop' -exec grep -H "Search string" {} \; 2>/dev/null  
For "Search string", substitute the label you see in the overview. For more specific results, prepend with "Exec=", e.g., type "name=Files" to find the desktop files that appear as "Files" in your overview. Once you know the file names, you can look at their contents to see what application they refer to. Eventually delete one you do not want to see anymore. Give preference to delete the ones under ".local/share/applications" rather than system wide .desktop files.

Having them appear twice would mean they are named differently

---

### Post by magunto on 2020-05-16
Thanks for the answer. So I did some cleaning and updates (bleachbit and apt upgrade) and then rebooted, and there are some changes - now I can move icons to another page (the page flips when moving up / down the screen). Also the icons in the grid are more separated (but still lot of screen on the sides not used in my opinion). I am enclosing a screenshot. The KDE-connect icons for example are duplicated with same description.

---

