---
title: "Glade Toolbox Problem"
date: 2012-05-12
forum: Programming Talk
---

### Post by etdsbastar on 2012-05-12
Hello there,

I installed glade from the repositories today. I am using Ubuntu Precise Pangolin.

It's weird but, the toolbox of glade is showing properly when the glade window is in normal stage. But, when I maximize the window... ....

the toolbar goes off the area and becomes completely unusable. Please see the screenshot.

Is there any way to solve this problem.

---

### Post by pbrane on 2012-05-12
I have the same problem. I have not found a solution to this bug yet, however if you change the palette view to text only or text with icons the tool palette seems to stay in view.

---

### Post by etdsbastar on 2012-05-12
> **pbrane said:**
> I have the same problem. I have not found a solution to this bug yet, however if you change the palette view to text only or text with icons the tool palette seems to stay in view.


That solved the problem. But not completely. Still, there are some performance issues.

---

### Post by pbrane on 2012-05-12
I have been experimenting with themes, this issue seems to be theme based. If I change the theme to NOX the palette works better. I have discovered that the palette stays in view as long as there is a scroll bar in the palette window. Glade does not seem to work correctly with any theme but some seem to work a little better than others.

EDIT: Maybe not theme based actually. But some themes seem to work better than others. I wonder if this has anything to do with ubuntu's back porting of some features from GTK-3 to GTK-2. Similar to the resize grip issue.

---

### Post by fallenshadow on 2012-05-12
Hmm... something I have noticed here.

Glade widget buttons seem to be contained in a Toolpalette. My own software project uses a Toolpalette too and a strange similar bug seems to happen on Ubuntu 12.04. (with the code unchanged since 11.10)

My buttons are visible if I make the height of the window really small, but will disappear if the height of the window is increased.

---

### Post by r-senior on 2012-05-12
> **fallenshadow said:**
> Glade widget buttons seem to be contained in a Toolpalette. My own software project uses a Toolpalette too and a strange similar bug seems to happen on Ubuntu 12.04. (with the code unchanged since 11.10)
I ran Fedora 16 with Gnome Shell for a short time and I used to get the same problem there too -- so it may be how Gnome 3 renders the GTK+ widget.

Just tried it on a Debian VM with Gnome Shell and get the same problem there too:

---

### Post by etdsbastar on 2012-05-12
So guys,

finally, what's the solution for this bug. I hope glade developers could solve this in their next version.

---

### Post by pbrane on 2012-05-12
> **r-senior said:**
> I ran Fedora 16 with Gnome Shell for a short time and I used to get the same problem there too -- so it may be how Gnome 3 renders the GTK+ widget.

Just tried it on a Debian VM with Gnome Shell and get the same problem there too:

I'm running Xubuntu 12.04, I suspect this is a GTK-3 issue. If you see the same problem in Fedora it's probably not an Ubuntu backport issue.

If one makes the window height small enough to bring up the scroll bars the toolpalette acts normally.

---

