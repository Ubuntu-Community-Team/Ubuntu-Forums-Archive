---
title: "[SOLVED] ctrl + alt + f1 or f2"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by xdarkday on 2008-06-19
I hit these thinking it was a different shortcut (switching my workspace)

please excuse my newb terms.

It seemed to log me out of gnome and to a "dos" like looking screen that looked like a command line just like terminal. I clicked something and it logged loaded a messed up gnome.

Ok, so it seems like maybe im in a safe mode gnome now or something. my screen resolution is messed up and video drivers dont seem to be working anymore. any idea what is going on here?

---

### Post by estamand on 2008-06-19
> **xdarkday said:**
> I hit these thinking it was a different shortcut (switching my workspace)

please excuse my newb terms.

It seemed to log me out of gnome and to a "dos" like looking screen that looked like a command line just like terminal. I clicked something and it logged loaded a messed up gnome.

Ok, so it seems like maybe im in a safe mode gnome now or something. my screen resolution is messed up and video drivers dont seem to be working anymore. any idea what is going on here?

You`ve just gone down to a terminal.  To get back to x-windows just press ALT-F7.

---

### Post by bodhi.zazen on 2008-06-19
> **estamand said:**
> You`ve just gone down to a terminal.  To get back to x-windows just press ALT-F7.

console :)

---

### Post by Duck2006 on 2008-06-19
To switch work spaces CTRL+ALT+(LEFT ARROW or RIGHT ARROW)

---

### Post by xdarkday on 2008-06-19
hmm it said it was in low res mode or something. I still cant seem to get to the regular old gnome load up.

:(

anymore suggestions? assume I know nothing.

---

### Post by xdarkday on 2008-06-19
Yeah i press alt+f7 at the console and it doesnt do anything. it just has a blinking "-".

---

### Post by tjwoosta on 2008-06-19
may be a dumb question but have you tried restarting?

---

### Post by RomeReactor on 2008-06-19
HI. As said before, CTRL+ALT+F1 will take you from your graphical desktop to a console; CTRL+ALT+F7 will take you from the console to your graphical desktop--assuming you didn't do anything to stop it. To reboot from the console:
```
sudo reboot
```
or
```
sudo shutdown -r now
```

---

### Post by Delever on 2008-06-19
There are different user spaces, which can be accessed with ctrl+alt+F* shortcut. Ubuntu graphical user interface runs on F7. That's what you press to get back. And it's safe to do.

---

### Post by xdarkday on 2008-06-19
Ok thanks for the replies, but I found out what happened. I was in the middle of messing around with my /etc/X11/xorg.conf file when i accidently used the wrong command keys to switch spaces (read first post). After that happened I had no idea how to get back to the actual gnome desktop, so i pressed the re-start button. I had to edit the /etc/X11/xorg.conf file to get my resolution back to normal, and re-enable my nvidia divers.

Thanks for the help everyone.

---

### Post by Dr Small on 2008-06-19
> **bodhi.zazen said:**
> console :)
+1
My favorite spot on the computer. :D

---

