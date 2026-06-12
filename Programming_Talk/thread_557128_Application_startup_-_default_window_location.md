---
title: "Application startup - default window location"
date: 2007-09-22
forum: Programming Talk
---

### Post by sabatier on 2007-09-22
Hi all,

Is there a way to change the startup script of a program like, say Gedit, to change
the default size and location of the window?

sabatier

---

### Post by MicahCarrick on 2007-10-02
This is an often debated topic in the GNOME development community. The way it is now, is:

The application is responsible for remembering the size and state (maximized) of the window and restoring it at startup.
The window manager (GNOME) is responsible for the position.

So, GNOME positions the window based on other open windows. The idea here is that if you had a dialog or another application open that wasn't before, GNOME will try to position the opening application so that it does not cover the existing dialog.

Some applications, such as Gedit, provide an option in the preferences dialog to have the program itself remember the position.

---

### Post by AlexThomson_NZ on 2007-10-02
There is a program called devilspie that I think can do what you want.  You can do things like start all programs called "Terminal" maximised, etc.

---

### Post by mssever on 2007-10-02
Beryl also can do at least some of what you want.

---

### Post by lubeck on 2008-01-14
Hello:
Important preference selection, indeed.
In GUTSY 7.10 I have discovered the solution in:

System
Preferences
Advanced Desktop Effects Settings (if installed from repository and active)
Window Management Area >  Place Windows 

Simply select "Center" in the tab labeled 'General' - or another selection you wish.
Regards.

---

### Post by xlinuks on 2008-01-14
That's not what ppl wanna hear, I just wanna comment a bit.
Ironically Gnome won't let you choose whether you want to obey its window rules or not (unless the program code positions itself).
I love Gnome but there are three main "ugly/cumbersome" things I hope get fixed, but for now gotta deal with:
1) The open/save file dialog (The worst design I had ever to deal with, though I heard somewhere changes are underway)
2) The windows position issue
3) The slow file manager (file navigation is slow, folder creation and alike run with slight delays) with BIG buttons, inability to select multiple files with the mouse (the list is pretty long).
From other points of view it beats both KDE and windows though. If I were a C programmer instead of a Java one I would certainly submit patches or redesign them. Nonetheless that's not enough, as one knows, you have also to convince those who own the project to accept your patches/code, this sometimes is the most difficult thing (Should I mention the "dialogs" between Linus and some ppl from the Gnome team?..)

---

### Post by Sak on 2008-03-03
Thought I'd update this post with a little tidbit I found that might be helpful for other users searching for this solution.  This advice works for Gutsy with Compiz enabled, and with the CompizConfig installed (instructions for getting CompizConfig are here [http://ubuntuforums.org/showthread.php?t=711321]("http://ubuntuforums.org/showthread.php?t=711321")).

Step-by-step for setting up a fixed window position here...

[http://phorolinux.com/quick-tip-configuring-fixed-window-placement-in-compiz-fusion.html]("http://phorolinux.com/quick-tip-configuring-fixed-window-placement-in-compiz-fusion.html")

Very useful for placing a specific window, such as a terminal, in the same place every time.  In my case I like to always have my terminal in the upper right corner.

Anyway, hope that helps.  :)

---

### Post by viralmeme on 2010-10-07
> **sabatier said:**
> Is there a way to change the startup script of a program like, say Gedit, to change the default size and location of the window?
[changing default starting position of windows]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/")

---

