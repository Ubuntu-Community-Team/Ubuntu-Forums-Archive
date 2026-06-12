---
title: "Remap End key to a spare key on my laptop"
date: 2018-02-20
forum: New to Ubuntu
---

### Post by Rvdpeet on 2018-02-20
Hi everyone,

I'm not really new to Ubuntu itself, but I am new to remapping keys.

I'm running Ubuntu 17.10 on my ASUS ROG GL553VD.

Although I love my laptop, there's one flaw (in my opinion) in the keyboard layout. The end key, which I often use, is located on the numpad on the 1-key, which means I have to turn off numlock in order to use my end key.

However, there is this spare key which I would like to give the function of the End key

I've tried xev and xmodmap, but couldn't find the package.

Can anyone tell my how to use the spare key as end key?

Thanks in advance!


Regards,
Rutgervdpeet

---

### Post by TheFu on 2018-02-20
How keys are remapped is extremely dependent on the DE used.  For example, I don't use any DE, but use openbox as the window manager, WM.  Openbox has an XML config file that lets me remap any keys to any commands desired.  
If you are using Gnome, I'd look for a Gnome tool to do remapping. [https://help.gnome.org/users/gnome-help/stable/keyboard-shortcuts-set.html.en](https://help.gnome.org/users/gnome-help/stable/keyboard-shortcuts-set.html.en) might be helpful. I don't know.

By default, 17.10 doesn't use X/Windows. It uses Wayland. I don't know how much this matters, but I suspect the gnome method will work regardless.

---

### Post by electrosteam on 2018-02-20
I had a very similar requirement on a Dell laptop used with LibreCad on Lubuntu 17.10.
I re-mapped one of the keys to the ESC function and added shortcuts on the desktop to simple scripts alternating between the functions.

This link is to my thread on the LibreCad Forum:

[http://forum.librecad.org/Mouse-on-LHS-ESC-Key-td5715482.html](http://forum.librecad.org/Mouse-on-LHS-ESC-Key-td5715482.html)

God luck, John.

---

### Post by Rvdpeet on 2018-03-09
Hi electrosteam,

Thanks a lot for your reaction. You put me on the right track and now I fixed it with Xmodmap.

Regards,
Rutger

---

### Post by HermanAB on 2018-03-12
You could also install a keyboard macro program such as Autokey and then assign whatever string you want to the spare key.

---

