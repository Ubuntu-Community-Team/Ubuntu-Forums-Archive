---
title: "terminal not working"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by RAJASD on 2011-10-30
im using netbook remix...
if i open terminal, it opens...i could type on it..
but after enter the one commandline, if i press enter it doest respond...cursor only stay in first line...
(my enter key working) 

need help...
thanks....

---

### Post by WasMeHere on 2011-10-30
Hi RAJASD,

Wonder if the Enter key is working. Try Ctrl + M instead (it should send an 'Enter' byte and launch your command in the terminal). If this works, then the problem is your Enter key. Otherwise it is something else.

Have fun finding out :-)
Olle

---

### Post by RAJASD on 2011-10-30
> **Olle Wiklund said:**
> Hi RAJASD,

Wonder if the Enter key is working. Try Ctrl + M instead (it should send an 'Enter' byte and launch your command in the terminal). If this works, then the problem is your Enter key. Otherwise it is something else.

Have fun finding out :-)
Olle

yeah ctrl+m working...but my enter key is fine...it is working
in other applications...
wat should b the reason?

---

### Post by WasMeHere on 2011-10-30
Strange! Could it be that you have a global binding, so that Enter is caught and performs some other task?

How are you invoking the terminal?
- as a window with  ctrl + alt + T  or
- as a text screen with  ctrl + alt + F3  or similar

---

### Post by RAJASD on 2011-10-31
> **Olle Wiklund said:**
> Strange! Could it be that you have a global binding, so that Enter is caught and performs some other task?

How are you invoking the terminal?
- as a window with  ctrl + alt + T  or
- as a text screen with  ctrl + alt + F3  or similar

im using by ctrl+alt+t.
but i tried with ctrl+alt+f3 enter key working.

i feel f3 way is not good. i cant minimize it. i want to work with window based one.
is there any way?

---

### Post by WasMeHere on 2011-10-31
I think there is a key binding, that catches your Enter key. I am not sure where in the menus to find the GUI to manage those bindings, but in gnome 2 you can run the program from a terminal with
```
gnome-keybinding-properties
``` [COLOR="Red"]If this is not the case for your ***netbook remix***, let us hope that someone using it reads this thread and helps you find out.[/COLOR]

---

### Post by RAJASD on 2011-11-05
> **Olle Wiklund said:**
> I think there is a key binding, that catches your Enter key. I am not sure where in the menus to find the GUI to manage those bindings, but in gnome 2 you can run the program from a terminal with
```
gnome-keybinding-properties
``` [COLOR="Red"]If this is not the case for your ***netbook remix***, let us hope that someone using it reads this thread and helps you find out.[/COLOR]

after i entered the code i got the window with 'keyboard short cuts'
then i closed it. output came like

(gnome-help:2314): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(gnome-help:2314): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(gnome-help:2314): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(gnome-help:2314): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

what shud i do?

onemore thing i jus want terminal for execute mysql otherwise i dont need it.
if u hav any idea about doing mysql in any other interface,pls tell me.
thanks

---

### Post by WasMeHere on 2011-11-05
> **RAJASD said:**
> after i entered the code i got the window with 'keyboard short cuts'
then i closed it. output came like
...
(gnome-help:2314): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

what shud i do?

onemore thing i jus want terminal for execute mysql otherwise i dont need it.
if u hav any idea about doing mysql in any other interface,pls tell me.
thanks
What about the window with 'keyboard short cuts'? Did you find a binding for your enter key? Look again, and if you find it, you can delete that binding or change it to something else. Maybe it works even if there is error output.

Otherwise you can 
1. Use ctrl + m in the terminal as it is now
2. Try if Enter works in the terminal window of xterm (included) or tilda (in the repositories)
```
xterm
``` or ```
sudo apt-get install tilda
tilda
```
3. Try some other terminal window (there are many of them)
[[COLOR="RoyalBlue"]_http://linuxreviews.org/software/x11-terms/_[/COLOR]]("http://linuxreviews.org/software/x11-terms/")

---

### Post by RAJASD on 2011-11-05
> **Olle Wiklund said:**
> What about the window with 'keyboard short cuts'? Did you find a binding for your enter key? Look again, and if you find it, you can delete that binding or change it to something else. Maybe it works even if there is error output.

Otherwise you can 
1. Use ctrl + m in the terminal as it is now
2. Try if Enter works in the terminal window of xterm (included) or tilda (in the repositories)
```
xterm
``` or ```
sudo apt-get install tilda
tilda
```
3. Try some other terminal window (there are many of them)
[[COLOR="RoyalBlue"]_http://linuxreviews.org/software/x11-terms/_[/COLOR]]("http://linuxreviews.org/software/x11-terms/")

thanks olle...

---

