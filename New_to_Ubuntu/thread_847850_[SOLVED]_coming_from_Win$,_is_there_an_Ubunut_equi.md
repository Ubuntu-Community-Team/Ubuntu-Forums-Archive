---
title: "[SOLVED] coming from Win$, is there an Ubunut equivalant to &amp;quot;win explorer&amp;quot; file manag"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Sudan on 2008-07-02
In Ubuntu is there an app that functions the same as the Windows Explorer?  

Is there a web page anywhere this lists for Windows users how you do the equivalent process in Ubuntu?

I need a file manager.  I'd like to see the partitions on the HD I just made when I installed Ubuntu.  And look at data files on my external USB HDs.   

I'm a real newbie - just today I scrubed Vista off the HD on this new computer and installed8.4  Ubuntu as my main operating system.  Worked like a breeze

---

### Post by drs305 on 2008-07-02
nautilus is the default ubuntu file browser. You can start it by typing 'nautilus' in a terminal or clicking on Places, Home Folder.

For partitions, gparted is the default app. Start it with:
**gksudo gparted**

When you use 'sudo' or 'gksudo' you will be asked for your password. You won't see it as you type but it is being recorded. Just hit Enter when you've typed it.

You need sudo or gksudo to gain permission to perform operations which require administrator privileges. gksudo is used for graphical applications while 'sudo' is used for terminal commands that won't invoke a graphical application.

Welcome to ubuntu !

---

### Post by Sudan on 2008-07-03
> **drs305 said:**
> nautilus is the default ubuntu file browser.

Thanks for helping.

---

