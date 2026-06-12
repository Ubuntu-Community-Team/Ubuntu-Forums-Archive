---
title: "How do I add Bookmarks on a Panel"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by darthjure on 2008-05-17
I've had Xubuntu on my laptop for a few weeks and love it.  It brought new life to this 500mHz Pentium III.

The top panel has Applications, Places, a launcher for Firefox and more.  I'd like to add URL links on there that will launch the browser and go to a website.  I have been able to add URL links on the desktop.  When I right-click the panel and click Add New Item, I don't see anything in that list of items that will let me add buttons for websites.  Is there some workaround I haven't figured out, or is there some way to add an item to that list of items that can go on the panel?

Thanks in advance for any help!

---

### Post by drs305 on 2008-05-17
Short Version:
Drag the address onto the panel and release! I have to click on the far left part of the web address in the browser window for it to 'grab' it.


Long Version (for any panel shortcut, really):
In ubuntu, and probably kubuntu, you can right click on the top panel, select 'Add to Panel', Custom Application Launcher. Enter a name for the shortcut and in the command window type your command - in this case the browser name and the web address. I use swiftweasel, so my command line in the custom luancher command window looks like this:
```
swiftweasel http://www.google.com
```

For the browser name, just make sure it is the same name as would open your browser in a terminal.

---

### Post by darthjure on 2008-05-17
That was too easy - didn't even require the terminal!  That was exactly what i was looking for.  Thanks!

---

