---
title: "Create shortcuts without going through the Terminal"
date: 2020-01-30
forum: New to Ubuntu
---

### Post by heqro on 2020-01-30
Hey!

My father has been recently asking me guidelines as to how to create shortcuts to his folders on Ubuntu. He is dramatically obsessed with order, and so he keeps his files organized under a handful of folders. He needs to do *a lot* of shortcuts so that he can access to everything without going through too much hassle, and he also needs to be able to delete some of them if due.

Right clicking over the file and searching for this feature (just like on Windows) yielded nothing, and he was really turned down by how he would have to open the Terminal every single time he wanted to create a desktop shortcut; this particular concern seems absolutely reasonable to me.

The question is the following: "Is there any **user-friendly** way to create shortcuts?" I have been searching the web for a while, yet I have not been able to found an application that could just simply throw in those two or three lines of code in the terminal for us whenever we needed it.

---

### Post by similar2 on 2020-01-30
Mark the folders as favorites or bookmarks them in Nautilus:
[https://www.omgubuntu.co.uk/2018/03/top-gnome-3-28-features](https://www.omgubuntu.co.uk/2018/03/top-gnome-3-28-features)
[https://ubuntuforums.org/showthread.php?t=2391762&p=13854939#post13854939](https://ubuntuforums.org/showthread.php?t=2391762&p=13854939#post13854939)
[https://itsfoss.com/add-remove-bookmarks-ubuntu/](https://itsfoss.com/add-remove-bookmarks-ubuntu/)

---

### Post by CatKiller on 2020-01-30
> **heqro said:**
> Right clicking over the file and searching for this feature (just like on Windows) yielded nothing, and he was really turned down by how he would have to open the Terminal every single time he wanted to create a desktop shortcut; this particular concern seems absolutely reasonable to me.

You're calling them shortcuts, but describing linked files. Linux is not Windows. The actual equivalent to Windows' shortcuts just uses a text editor, and makes all the launchers that you get in menus and on the panel, and so on. Linked files are part of the filesystem and access the same data through two different files.

In KDE, which is what I use, the file browser pops up a menu whenever you drag-and-drop a file, asking you what action you want to perform. In Gnome, the file browser will pop up that menu if you middle-click-and-drag, or you can hold one of the modifier keys as you click-and-drag to tell it which action you want to do without the menu. Other desktop environments and other file browsers will have similar methods to do the same thing.

In neither case do you need to use the command line.

---

### Post by heqro on 2020-01-31
> **CatKiller said:**
>  In Gnome, the file browser will pop up that menu if you middle-click-and-drag, or you can hold one of the modifier keys as you click-and-drag to tell it which action you want to do without the menu.

I tried this on Ubuntu, and the first option didn't seem to do anything besides just copying the folder into the Desktop; sadly, I realized about that when I found out that the system took a really, really long time just to make a 1KB shortcut for a 23GB folder.

On the other side, what is a modifier key?

---

### Post by CatKiller on 2020-01-31
> **heqro said:**
> On the other side, what is a modifier key?

Ctrl, Alt, Shift, Meta (Win-key). It's been a while since I used Gnome, so I can't remember which one does what; *copy, move, create link, open the menu* are the options, indicated by a change in the mouse pointer. I think at least one of the options needed you to be holding two modifier keys.

---

### Post by vanadium on 2020-02-01
"Shortcuts" and "links" are two different things. "Shortcuts" are text files with the .desktop extension that execute an application, or also can open a file in an application. "Links" are, as  "CatKiller" indicated, references to other files that for practical purposes act and behave as a real file existing on the location where the link is.

Unfortunately, shortcuts for files and folders on the desktop or elsewhere, which were brought to us through Windows 95, are not anymore well supported in recent Linux versions. Any graphical way to create a shortcut to a file have been removed. I am not sure if other desktops such as XFCE (Xubuntu) or KDE (Kubuntu) still has good support for file shortcuts. Links, on the other hand, are still supported although the graphical option to create them is hidden in a default Ubuntu install. One has to enable the menu option in the preferences.

Rather than spending time organizing shortcuts, the time might be better spend organizing the actual files. As indicated before, bookmarks allow quick access to folders that are frequently used. The search feature in Files also allows to move to a specific folder in seconds. The "Recent" tab in Files, in File Open dialogs and in many applications allows you to quickly select one of the files you recently worked on. All that avoids the need to have a "double housekeeping" of manually organizing shortcuts next to organizing your actual files.

---

