---
title: "how to create new folders?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by pardesi on 2008-04-26
this might be the dumbest question but how does one create new folder on ur desktop with kde 4.0 .When one right clicks there is no option of creating new folders:guitar:

---

### Post by Michael.Godawski on 2008-04-26
Well you can use the terminal. Navigate to the Desktop directory and run:
```
mkdir name
```

---

### Post by pardesi on 2008-04-26
how to navigate to the desktop

---

### Post by Michael.Godawski on 2008-04-26
When you open up the terminal run

```
ls
```

This should give you something like:
```
michael@michael-laptop:~$ ls
Desktop    Examples  nautilus-debug-log.txt  Public     Videos
Documents  Music     Pictures                Templates
michael@michael-laptop:~$ 
```

the ls command list all directories and folders in the current directory so the navigation is easier.
now run:

```
cd Desktop
```
and then 
```
mkdir name
```

---

### Post by salemboot on 2008-09-28
The guy wanted to know how to do it graphically from within KDE 4.

Apparently you can't create new folders on the desktop.

You have to use dolphin.  

Which reminds me of blackbox.  If I want to run that sort of way I'll just stick with blackbox.

4.0 KDE is a culture shock.  

> **Michael.Godawski said:**
> When you open up the terminal run

```
ls
```

This should give you something like:
```
michael@michael-laptop:~$ ls
Desktop    Examples  nautilus-debug-log.txt  Public     Videos
Documents  Music     Pictures                Templates
michael@michael-laptop:~$ 
```

the ls command list all directories and folders in the current directory so the navigation is easier.
now run:

```
cd Desktop
```
and then 
```
mkdir name
```

---

### Post by skullmunky on 2008-09-28
That is not a dumb question at all.  KDE4 breaks about 20 years of assumptions about how the desktop works, namely that you can, ah, put folders on it. 

By default KDE4 does NOT show your "Desktop" folder at all.  If you had KDE3 and then installed KDE4 it will turn everything that you HAD on the desktop into little file launcher widgets, but that's not really too helpful.

Here's what you probably want to do:

Add a "Folder View" widget to the desktop.  by default this shows your "Desktop" folder, but you can also configure it to show your Home folder, or anything else.  You can also have many of these, that show different folders.

Now you can right-click in the Folder View widget and it'll let you create new folders, files, links, etc. like normal.

Double-clicking a folder will open it in Dolphin.

---

### Post by erwinsoo on 2008-12-06
in ubuntu 8.10 while in the file explorer, at the top switch to icon view instead of list view.. right click on any empty space and you will see the option to create new folders. In list view, if the list of files exceeds that of the window, no empty space is available for right clicking

---

### Post by liviubero on 2009-06-27
Although this thread is an old one, here is another way to create folders on the desktop.
One can set up the kde 4 desktop to show just a "desktop", i.e. a background image with widgets on it, or to show a folder view (traditional desktop).
Right click on the desktop, choose Appearance Settings. Choose by "Type" the "Folder View" option. This will turn the "desktop" into your old friend folder-view-desktop. Then you can create folders or files as usual by right clicking on it and choosing New->Folder.

---

