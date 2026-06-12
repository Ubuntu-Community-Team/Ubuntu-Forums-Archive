---
title: "[SOLVED] Apps at startup"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2008-09-20
Hi,
I just came across a website that had some awesome tweaks to Ubuntu. One of them is a launch bar similar to what Mac users have. Its called Avant Windows Navigator. AWN for short.
Problem is that when I restart Ubuntu, it is gone, and when I run AWN manually (from Appplications > Accessories > Avant Windows Navigator), some of the applications launchers are missing and I have to add them again. Sort of spoils the fun :(

What I want to know is how to run this app at startup. I know that if I go to System > Preferences > Sessions > Startup programs > add.. I think I should be able to set a new applicaiton such as AWN to start automatically when Ubuntu starts up. Where are apps kept? i.e. what file do I point to in the 'add' dialogue. Or more accurately, where are these files kept?

Having only recently converted from Windows, they would keep all the exe's under system/programs/...
Where does Ubuntu keep them?

I tried usr/share/applications/.... where there seem to be all the applications, but AWN selected from here does start at startup.

Can someone help please

---

### Post by howefield on 2008-09-20
> **steinzeitmensch said:**
> What I want to know is how to run this app at startup.

you're correct about how to add the launcher to your startup routine.

In the name field type whatever you want.
In the command field type avant-window-navigator.
In the comments field type whatever you want.

---

### Post by steinzeitmensch on 2008-09-20
Hey, thanks
I did not realise that it would be so stright forward. **** the windows way is more complicated.
Does this mean that all apps in Linux are somehow known by there name meaning that there is no need to give paths to applications, but mearly just 'quote thier names'?
If that is right, how cool.
anyway, thanks for the hand

---

### Post by Mornedhel on 2008-09-20
> **steinzeitmensch said:**
> Does this mean that all apps in Linux are somehow known by there name meaning that there is no need to give paths to applications, but mearly just 'quote thier names'?

They have full paths all right, but there is a shortcut to them. If you are curious, you can open a terminal and type echo $PATH : this prints a list of all locations where your usual executables will be looked for. All commands and programs who live in those folders can be called by their "name". You can add entries to your PATH if you have specific needs (for instance, if you maintain a folder full of nifty Bash scripts you've written yourself).

Also, typing which [program name] prints their location, for instance :

which ls

prints '/bin/ls', which is the full path you'd need to use otherwise.

---

### Post by howefield on 2008-09-20
> **steinzeitmensch said:**
> Does this mean that all apps in Linux are somehow known by there name meaning that there is no need to give paths to applications, but mearly just 'quote thier names'?

Many are, but not all, one way of finding out the command, is to drag the application icon from the menu to the desktop, right click the icon on the desktop and select properties. Select the Launcher tab and hey presto.

---

