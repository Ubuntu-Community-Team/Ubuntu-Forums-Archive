---
title: "HOW TO Embed terminal on Desktop using Compiz Fusion"
date: 2010-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jonathan_ender on 2010-12-28
I was able to get an embedded terminal on desktop (terminal as wallpaper) by doing the following: 


go to terminal:
Edit->Profiles->New

name it "desktopconsole_1"

Under *General* tab, uncheck "Show menubar by default in new terminals".

Under *Background* tab, choose "Transparent background". The scroll is set to "None".

Under *Scrolling* tab, select "Disabled".

Under *Title and Command* tab, set "Initial title" to "desktopconsole_1" and set "When terminal commands set their own titles" to "keep initial title"


Then go to CompizConfig Settings Manager(Make sure you have it installed if you don't):

Under ***Window Decoration***, add "!title=desktopconsole_1" to the *Decoration Windows *field

Under ***Window Rules***, add "title=desktopconsole_1" to the fields:

Skip taskbar
Skip pager
Below, Sticky
Non resizable windows
Non minimizable windows
Non maximizable windows
Non closable windows

In the* Size rules *tab, add "title=desktopconsole_1" and set the desired width and height.

Under the *Place Windows* tab->Fixed window placement->Windows with fixed positions; add "title=desktopconsole_1" with desired position (0,0 is the top left corner)

To get this on startup:

System->Preferences->Startup Applications; add gnome-terminal as name (or anything you want) and under command : "gnome-terminal --window-with-profile=desktopconsole_1"

I was wondering if there was a way to do this the same way but by using a config file or scripts so that that process is more reproducible? Or maybe a more elegant way without the GUI but without the usual devilspie way?

Reference:

[http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html](http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html)

[https://wiki.archlinux.org/index.php/Terminal_as_a_Transparent_Wallpaper](https://wiki.archlinux.org/index.php/Terminal_as_a_Transparent_Wallpaper)

---

### Post by K9Crunch on 2011-01-04
Thank you for posting this, I was looking for new and updated instructions on how to do this in Maverick.

---

### Post by crownedzero on 2011-01-12
Working nicely except I dont have a 100% transparent terminal. I still have a title bar at the top of the terminal as well as a "border". Any ideas on how to fix this?

---

### Post by lewisskinner on 2011-01-13
This is great!  My terminal is 100% transparent.  However, I now seem to have no titlebar for any of my windows!  Have I accidentally switched something else off in the process of doing this?

Also, any way to make this start on a different desktop (for preference, I'd have it on 4).

**EDIT**

Also, need it fixed to desktop.  Essentially at the moment, we're asking compiz to open a window on login.  I could do that via *system -> preferences -> startup applications*, just setting default profile as transparent.

Ideally, I'd want something more like [this](http://ubuntuforums.org/showthread.php?t=202249):

[http://img135.imageshack.us/img135/7796/desktopterminal6vw.png](http://img135.imageshack.us/img135/7796/desktopterminal6vw.png)

---

### Post by zyiro on 2011-01-14
> **lewisskinner said:**
> This is great!  My terminal is 100% transparent.  However, I now seem to have no titlebar for any of my windows!  Have I accidentally switched something else off in the process of doing this?

Also, any way to make this start on a different desktop (for preference, I'd have it on 4).

**EDIT**

Also, need it fixed to desktop.  Essentially at the moment, we're asking compiz to open a window on login.  I could do that via *system -> preferences -> startup applications*, just setting default profile as transparent.

Ideally, I'd want something more like [this](http://ubuntuforums.org/showthread.php?t=202249):

[http://img135.imageshack.us/img135/7796/desktopterminal6vw.png](http://img135.imageshack.us/img135/7796/desktopterminal6vw.png)

im having the same issue when i add "title=desktopconsole_1" to window decorations it removes the decoration for all windows....

---

### Post by hbaromega on 2011-01-18
> **jonathan_ender said:**
> I was able to get an embedded terminal on desktop (terminal as wallpaper) by doing the following: 


go to terminal:
Edit->Profiles->New

name it "desktopconsole_1"

Under *General* tab, uncheck "Show menubar by default in new terminals".

Under *Background* tab, choose "Transparent background". The scroll is set to "None".

Under *Scrolling* tab, select "Disabled".

Under *Title and Command* tab, set "Initial title" to "desktopconsole_1" and set "When terminal commands set their own titles" to "keep initial title"


Then go to CompizConfig Settings Manager(Make sure you have it installed if you don't):

Under ***Window Decoration***, add "!title=desktopconsole_1" to the *Decoration Windows *field

Under ***Window Rules***, add "title=desktopconsole_1" to the fields:

Skip taskbar
Skip pager
Below, Sticky
Non resizable windows
Non minimizable windows
Non maximizable windows
Non closable windows

In the* Size rules *tab, add "title=desktopconsole_1" and set the desired width and height.

Under the *Place Windows* tab->Fixed window placement->Windows with fixed positions; add "title=desktopconsole_1" with desired position (0,0 is the top left corner)

To get this on startup:

System->Preferences->Startup Applications; add gnome-terminal as name (or anything you want) and under command : "gnome-terminal --window-with-profile=desktopconsole_1"

I was wondering if there was a way to do this the same way but by using a config file or scripts so that that process is more reproducible? Or maybe a more elegant way without the GUI but without the usual devilspie way?

Reference:

[http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html](http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html)

[https://wiki.archlinux.org/index.php/Terminal_as_a_Transparent_Wallpaper](https://wiki.archlinux.org/index.php/Terminal_as_a_Transparent_Wallpaper)




This we can do just by setting the terminal. What's extra is compiz doing?

---

