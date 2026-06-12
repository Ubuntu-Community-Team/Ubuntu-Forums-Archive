---
title: "Rewriting Caffeine with GtkBuilder"
date: 2009-07-20
forum: Programming Talk
---

### Post by Nevon on 2009-07-20
I'm currently working on a completely rewrite of the application Caffeine. If you don't know what it is, here's a short introduction: *Caffeine is basically a tray applet that allows you to easily disable your screensaver and the sleep power management mode. You can also disable it temporarily and have it automatically come back on after a duration that you set. Currently we have full support for gnome-screensaver and Kscreensaver. We're working on support for Xscreensaver and just plain DPMS.*

Anyway, the code base for version 0.2 and below is just plain terrible. We're mixing and matching object oriented code with procedural code, and the GUI elements are all mixed with the code here and there. 

So what I would like to do is rewrite the code in an object oriented fashion, using GtkBuilder to separate the logic from the GUI. As the application grows, not being able to use glade to build the dialogs is a big pain. 

The problem is that I'm not so confident in my programming skills when it comes to object orientation (at least not structuring it from scratch), and I have never used GtkBuilder before.

I have built the entire application in glade (except for connecting signals with handlers), and I have managed to get the about dialog and the preferences dialog to work when I was first just testing it out. However, now I'm stuck with the new version.

If you look at the attached .xml-file (open it in glade to see it in all its glory) you'll see that I have i status icon in there. I've set the visibility to "on", yet when I run the application nothing happens. I can't really move forward without it, so I'm kind of stuck at the moment.

If there's someone with experience dealing with GtkBuilder, I would really appreciate any help you can give me. If you are interested in helping out in a more official sense, we are always looking for people who can join the project! 

To see the working application, run the following in a terminal:
```
bzr branch lp:caffeine
```

And to get the files I'm working on. (In another directory) run:
```
bzr branch lp:~reklamnevon/caffeine/rewrite
```

---

