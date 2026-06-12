---
title: "Would Like to Try new windows manager CTWM"
date: 2019-10-14
forum: New to Ubuntu
---

### Post by ranice on 2019-10-14
Hello all,

I am new to Ubuntu and have been looking around for a nice windows manager to use that I can customize to look the way I want it to look. So far I have come across CTWM and I really like it, however after installing it (using [FONT=courier new]sudo apt install ctwm[/FONT]) and logging off, I am unable to switch sessions to use CTWM. 

Am I doing something wrong? Or is there another way that I have to switch window mangers that I am unaware about? I am so confused...

---

### Post by cruzer001 on 2019-10-14
Hello ranice

CTWM is a xWindow manager
[https://en.wikipedia.org/wiki/X_window_manager](https://en.wikipedia.org/wiki/X_window_manager)
and probably not well suited for your needs.

If your trying to install it on Ubuntu-gnome it will not work out of the box and if you manage to get it working I do not expect it to integrate well with Gnome.

Do a search on **gnome 3 window manager** to get a better understanding.

I do run a xWindow system, but it was built to run nothing else but x.

---

### Post by TheFu on 2019-10-14
I assume you tried using the "gear" button on the login page before actually logging in?

---

### Post by cruzer001 on 2019-10-14
> **TheFu said:**
> I assume you tried using the "gear" button on the login page before actually logging in?
Hello TheFu
It does not appear at boot up on a gnome3 install and thats as far as I went.

---

### Post by deadflowr on 2019-10-14
I see it doesn't ship with a xsession *.desktop file which is needed for it to show in the login screen as an option.
Probably can start from a tty-esque session with startx.
May or may not require additional settings in an .xinitrc file for your user.

---

### Post by cruzer001 on 2019-10-14
Your right deadflowr

startx /usr/bin/ctwm

and it boots

---

### Post by cruzer001 on 2019-10-14
So ranice

At the login screen press
Ctrl + Alt + F3
and then login

Then enter
```
startx /usr/bin/ctwm
```
That will allow you to play with it.

---

### Post by deadflowr on 2019-10-14
I had to step out for a second but I tried this quickly
Created the desktop file
```
[Desktop Entry]
Name=CTWM
Type=Application
TryExec=/usr/bin/ctwm
Exec=ctwm
```
that would create a barebones desktop file.
then just save it to /usr/share/xsessions as ctwm.desktop
Here's another more impressive  (and quite over the top) .desktop file
[https://github.com/bbidulock/xde-session/blob/master/data/share/xde/xsessions/ctwm.desktop]("https://github.com/bbidulock/xde-session/blob/master/data/share/xde/xsessions/ctwm.desktop")

FWIW, .desktop files only actually require the Name the Type and the Exec lines.
But there are a lot of extra options too, if you want to play around.

---

### Post by cruzer001 on 2019-10-14
OpenBox is a popular choice and supports gnome.  I do not use it, but support for OB can be found here at our forums.
[http://openbox.org/wiki/Main_Page](http://openbox.org/wiki/Main_Page)

Another full featured xWM is FVWM.  Again I have yet to use it, but TheFu speaks highly of it.
[http://www.fvwm.org/](http://www.fvwm.org/)

Both are in our Ubuntu repositories.

Just something to keep in mind if you care to explore.

---

### Post by ranice on 2019-10-19
> **cruzer001 said:**
> So ranice

At the login screen press
Ctrl + Alt + F3
and then login

Then enter
```
startx /usr/bin/ctwm
```
That will allow you to play with it.

Ok I will try this

---

### Post by ranice on 2019-10-19
> **deadflowr said:**
> I see it doesn't ship with a xsession *.desktop file which is needed for it to show in the login screen as an option.
Probably can start from a tty-esque session with startx.
May or may not require additional settings in an .xinitrc file for your user.

I'm so sorry but I don't really understand what you're saying because I'm new to all of this :(

---

### Post by ranice on 2019-10-19
Ok, will do more research on how gnome works.

---

