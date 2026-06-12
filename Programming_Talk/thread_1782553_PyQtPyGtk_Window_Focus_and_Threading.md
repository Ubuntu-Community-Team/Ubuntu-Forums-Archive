---
title: "PyQt/PyGtk Window Focus and Threading"
date: 2011-06-14
forum: Programming Talk
---

### Post by ngrieb on 2011-06-14
I have an PyGtk applet I have been working on for a million years that constantly fails. I have been trying to repackage it into PyQt to make things easier, but I need a 2 main pieces to complete the puzzle. 

1. I have a QDialog window that gives the user information when the applet icon is hovered over. I want to be able to give this window focus and have the QDialog kill itself when focus is lost. How can I determine when the focus is gained/lost for a PyQt window?

2. I need to run a few subprocesses/threads from the PyGtk applet when it is initialized. I have built 2 PyQt classes that simply need to be initialized when the applet is started. How do I bypass the main loop and allow processes to run freely in the background till needed?

---

### Post by ngrieb on 2011-06-15
Is there a way to create a panel applet using another means under GNOME?

---

### Post by ngrieb on 2011-07-08
Can anyone show me how to use a pygtk GUI loop in order to allow for a subwindow to run without a segfault occurring? I just need a mouse over window to appear while hovering over an icon, once the icon is no longer in focus the subwindow should be killed.

The problem right now is that the enter-notify command keeps looping while the other window is looping, when you use a leave-notify event and then leave the icon a segfault occurs. 

Thanks.

---

