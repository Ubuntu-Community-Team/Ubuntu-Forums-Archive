---
title: "Creating my own desktop widget"
date: 2011-08-30
forum: Programming Talk
---

### Post by c0dehunter on 2011-08-30
So I am developing (or starting to develop) my own desktop widget to control system shutdown with timer. I am aware of Screenlets where you can make your own widget using Python but I'm not sure this is good for end user since he/she needs to install Screenlets first to show my widget. Instead I would like to create a standalone widget (like Conky, but far more simple). 
What framework or programming language can I use?
It is important that the widget isn't a standard program (like QShutdown), instead it must be visible just on desktop (like Conky, as said before) and I would need some buttons on it for user interaction.

---

### Post by hakermania on 2011-08-30
I have no idea how to make this, but with a quick look I saw that conky is written in C, give its source a try ;)
```

apt-get source conky

```

---

### Post by c0dehunter on 2011-08-31
Thanks, will look into it.

Any other tip is welcomed.

---

### Post by Habitual on 2011-08-31
Does it have to be conky?

If not, you can create a shutdown|restart|logout program using yad (fork of zenity)

[http://groups.google.com/group/yad-common/browse_thread/thread/bc97fa0537cc06ea/a8e81e0d3c32fed7?lnk=gst&q=shutdown#a8e81e0d3c32fed7](http://groups.google.com/group/yad-common/browse_thread/thread/bc97fa0537cc06ea/a8e81e0d3c32fed7?lnk=gst&q=shutdown#a8e81e0d3c32fed7)

has the code.

---

### Post by c0dehunter on 2011-08-31
Habitual, no, it doesn't need to be conky, that was just an example.

Now this (yad) is a really helpful tip, going to check it immediately.  Thanks!

Also, if anyone knows any other alternative please post so I can rewise my options and choose one that best suits me.

**// EDIT:**
**I just realized that it is hard or impossible to build a widget with Yad. Im not sure if it's flexible enough so i could hide the widget when other windows are on-top and make it transparent. Or am I wrong here? ("zenity/yad transparency" has no viable results in Google :))**

---

### Post by Habitual on 2011-09-01
the yad 'applet' you create is not modal by default, so other windowed programs would just overlay it. It would be "hidden" so-to-speak.

barring that you could make it --undecorated and position it anywhere on the visible screen/workspace.

But if you are shutting down, or logging off|changing users, does it matter if it's transparent? It's just going to get clicked and close?

You could make a shortcut to this said 'applet' in the panel...?
Unobtrusive and out of the way...or assign a hotkey. But the panel already has an applet of this function, so I guess I am missing the goal of the task.

Sorry about that.

---

### Post by ofnuts on 2011-09-02
> **c0dehunter said:**
> So I am developing (or starting to develop) my own desktop widget to control system shutdown with timer. I am aware of Screenlets where you can make your own widget using Python but I'm not sure this is good for end user since he/she needs to install Screenlets first to show my widget. Instead I would like to create a standalone widget (like Conky, but far more simple). 
What framework or programming language can I use?
It is important that the widget isn't a standard program (like QShutdown), instead it must be visible just on desktop (like Conky, as said before) and I would need some buttons on it for user interaction.
You can have a look at KDE's kshutdown application

---

### Post by Habitual on 2011-09-02
"system shutdown **with timer**" - as usual Evelyn Wood's course left me hanging. :)

---

### Post by alegomaster on 2011-09-02
I have barely any experience with GUI's so please don't flame me, but wouldn't the widget have to be ported to each GUI, or is there an api with designing widgets on GUI's in Linux.

---

