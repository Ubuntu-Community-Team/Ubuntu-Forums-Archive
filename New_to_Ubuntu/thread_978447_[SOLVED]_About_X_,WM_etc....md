---
title: "[SOLVED] About X ,WM etc..."
date: 2008-11-11
forum: New to Ubuntu
---

### Post by FearlessPc on 2008-11-11
Hello there

I'm a little confused about all the levels of window making in Linux.
I'll write down what i have figured so far and some questions.

1) X window system - it allows to draw windows, but don't draw them herself ? , can i run Linux with only X without any Window Manager and still work in a window environment ?

2) on top of X comes Window Managers - which actually draws the windows and by the name of it its also manages the windows , so the X system don't manages the windows its not really in control of theme ?

3) on top of WM comes the Desktops - which are a bunch of common user applications , and thats it ? , can i combine any WM with any Desktop ?

4) GTK+ - i understand GTK+ is an API but where GTK engines fit in all this ? , and whats the difference between them ?

Thats it for now :)

Thanks is advance and excuse my english

---

### Post by kerry_s on 2008-11-11
> **FearlessPc said:**
> Hello there

I'm a little confused about all the levels of window making in Linux.
I'll write down what i have figured so far and some questions.

1) X window system - it allows to draw windows, but don't draw them herself ? , can i run Linux with only X without any Window Manager and still work in a window environment ?

2) on top of X comes Window Managers - which actually draws the windows and by the name of it its also manages the windows , so the X system don't manages the windows its not really in control of theme ?

3) on top of WM comes the Desktops - which are a bunch of common user applications , and thats it ? , can i combine any WM with any Desktop ?

4) GTK+ - i understand GTK+ is an API but where GTK engines fit in all this ? , and whats the difference between them ?

Thats it for now :)

Thanks is advance and excuse my english

1. no
2. yes
3. not sure what you mean. you can use a wm and add what ever you want to get it how you want. for example: i use jwm, it's a window manager, but it has most of the things that a desktop would have, meaning it has a taskbar, it can draw it's own background, it can do launchers, etc...
where as for example fluxbox, you need a program to put backgrounds, you need a program for desktop icons, forget panel launchers, you would need a different kind of panel, etc...
4. gtk engines is the decoration for gtk based programs.

---

### Post by 3rdalbum on 2008-11-11
> **FearlessPc said:**
> 1) X window system - it allows to draw windows, but don't draw them herself ? , can i run Linux with only X without any Window Manager and still work in a window environment ?

A good way to think of X is that it only allocates squares for other programs to draw into. It also manages keyboard and mouse input, and once all programs have drawn into their squares, X sends the finished product to the monitor.

> 2) on top of X comes Window Managers - which actually draws the windows and by the name of it its also manages the windows , so the X system don't manages the windows its not really in control of theme ?

Correct - the Window Manager allows windows (squares that programs can draw into) to be moved, resized, and temporarily hidden. It also takes keypresses from X and makes sure they go to the right place.

To answer your earlier question, you can run Linux and X without a window manager, but you cannot move or resize any of the windows on-screen. And if you open a text editor and start typing, your keystrokes will disappear into a black hole. Save all your work and turn off the window manager (you will pretty much need to restart once you've tried this):

```

killall metacity
killall compiz

```

> 3) on top of WM comes the Desktops - which are a bunch of common user applications , and thats it ? , can i combine any WM with any Desktop ?

Correct. Compiz is a window manager but not part of the Gnome project, yet you can easily run Compiz within Gnome. Or within XFCE. Or KDE. If you install yet another window manager like, say, Openbox, you can switch to it via the following command:

```
openbox --replace
```

Try it if you want, it won't cause any harmful effects.

> 4) GTK+ - i understand GTK+ is an API but where GTK engines fit in all this ? , and whats the difference between them ?

GTK engines take the API commands and draw the actual "widgets" (scrollbars, buttons, menus, text fields etc) according to their own code. The main difference between the GTK engines is what calculations they use to draw the widgets, different colours and special effects.

---

### Post by The Cog on 2008-11-11
1)
Yes you can run X applications without a window manager but it's hard work. You can't move or resize the windows because they don't have borders/decorations. They all go top-left. And the last one to open is the one in front of all the others. To get to the ones behind, you have to close the ones on front again. So in practical terms, no.

2)
It is the window manager that puts the decorations on the windows - borders, title bar etc. And you need those to move the windows around, resize them and bring the one you want to the front.

3)
I think you're right, but I'm not really sure. 

4)
GTK+ is a library of widget-drawing utilities - textboxes, scrollbars, buttons and things that go inside an application window. GTK+ presumably uses different 2D graphics libraries depending on the underlying OS's graphics capabilities, but again I'm hazy here.

---

### Post by FearlessPc on 2008-11-12
Thank you all for the fast replays ,i understand it better now.

I did tried the commands after installing different window managers and desktops. 

After finding this [site]("http://xwinman.org/") i see there is a lot more to explore...

---

