---
title: "[SOLVED] hiding icons"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by leemajors on 2008-06-20
Hi,

The external USB drives i use to store a lot of my stuff are working perfectly -- that is, ubuntu is very nicely detecting them and mounting them. It's also providing icons to them on the desktop -- which is what I want to find out how to avoid.

How do I continue having ubuntu mount the USB drives and have them made available in the "places" area in the file explorer but *not* have them sitting on my dektop?

---

### Post by Duck2006 on 2008-06-20
You will have to change the mount point. This may help.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by sdennie on 2008-06-20
Rather than changing the mount points, you can hit Alt-F2 and type gconf-editor.  Navigate to /apps/nautilus/desktop and uncheck volumes_visible.

---

### Post by leemajors on 2008-06-20
> **vor said:**
> Rather than changing the mount points, you can hit Alt-F2 and type gconf-editor.  Navigate to /apps/nautilus/desktop and uncheck volumes_visible.

lol, remember you're in absolute beginner talk here -- you gotta explain what these commands do. i hit alt+f2 and it sent me to a fullscreen terminal window and i didn't know how to get back out so i had to restart.

what is alt+f2 and for future reference, how do you get back to the gui?

---

### Post by Duck2006 on 2008-06-20
Command line. So you can run commands with out opening a terminal.

---

### Post by sdennie on 2008-06-20
You must have hit Ctrl-Alt-F2.  You just need to hit Alt-F2 which will bring up a "Run" dialog box.  Alternatively, you can just go to Applications->Accessories->Terminal and type "gconf-editor" into it.

For future reference, if you find yourself at the screen where you were, you can get back to the GUI with Ctrl-Alt-F7.

---

### Post by leemajors on 2008-06-20
great :) thanks!

what am i technically in when i hit ctrl+alt+f2?

---

### Post by sdennie on 2008-06-20
> **leemajors said:**
> great :) thanks!

what am i technically in when i hit ctrl+alt+f2?

It's called a console.  You can think of it as a terminal window except that it's the only thing on the screen.  The GUI (called X), almost always runs on the 7th console (which is why hitting Ctrl-Alt-F7 will get you back to it).

---

