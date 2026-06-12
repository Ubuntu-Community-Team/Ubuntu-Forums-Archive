---
title: "HOWTO: Change Window Manager in Ubuntu Feisty (GNOME)"
date: 2007-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by wersdaluv on 2007-06-04
First, download the Window Manager.

Then, just create a file named ".gnomerc" under your user folder containing this text
```
export WINDOW_MANAGER=/usr/bin/*name of Window Manager*
```

or simply enter this code in the terminal
```
echo export WINDOW_MANAGER=/usr/bin/*name of window manager* >> ~/.gnomerc

```

Enjoy!

*I got the idea here--> [http://doc.gwos.org/index.php/Xfwm4](http://doc.gwos.org/index.php/Xfwm4)

---

### Post by xyverz on 2008-07-23
Thank you for that.  I've been searching google for the last hour and finally stumbled on this one - which is the only solution that still worked.  :-)

---

### Post by wersdaluv on 2008-07-24
Wow. This thread has been here for quite a long while. A reply, at last. hehe

---

### Post by Bluehorn on 2009-09-20
> **wersdaluv said:**
> 
Then, just create a file named ".gnomerc" under your user folder containing this text
```
export WINDOW_MANAGER=/usr/bin/*name of Window Manager*
```or simply enter this code in the terminal
```
echo export WINDOW_MANAGER=/usr/bin/*name of window manager* >> ~/.gnomerc

```Enjoy!

*I got the idea here--> [http://doc.gwos.org/index.php/Xfwm4](http://doc.gwos.org/index.php/Xfwm4)

I ran into the same problem today. Compiz does not work correctly here and I don't need thate eye candy. Running ```
metacity --replace
``` fixed the running session, but after logout I was back at compiz.

After some searching, I found the gconf entry ```
/desktop/gnome/session/required_components/windowmanager
```, which pointed to ```
gnome-wm
``` on my system. That scripts contains the following comment:

```

# NOTE: DON'T USE THIS.  Please have your window manager install
# a desktop file and change the gconf key
# /desktop/gnome/session/required_components/windowmanager

```Setting the windowmanager key in ```
gconf-editor
``` in fact fixed my problem, and I now get metacity when logging into a Gnome session. Shouldn't there be a entry in the System menu for doing this?

---

### Post by stolk on 2009-11-06
Thanks! That worked for me. I don't know why it happened but it's fixed now! :D

---

