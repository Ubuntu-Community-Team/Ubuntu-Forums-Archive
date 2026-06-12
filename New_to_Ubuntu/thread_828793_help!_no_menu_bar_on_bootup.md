---
title: "help! no menu bar on bootup"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by hiro nakamatty on 2008-06-14
hi, i booted Ubuntu hardy heron up this morning, and when i logged on, there was no menu bar at the top and bottom of the screen. can any1 help, it would be greatly appreciated.
thanks, Matty :confused:

---

### Post by adityakavoor on 2008-06-14
Hit Alt+F2 and type 
```


gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

```

---

### Post by hiro nakamatty on 2008-06-14
sorry, but when i hit alt+F2, it doesn't do anything
thanks

---

### Post by msayed2004 on 2008-06-14
Try to restart your PC.
Alt+F2 type```
gnome-terminal
```this will open the terminal, execute```
sudo reboot
```or restart your X by Alt+Ctrl+Backspace.
If nothing happened open the terminal again & execute```
gnome-panel
```& tell us what it say.

And take a look @ [Working With Panels]("http://linux.about.com/library/gnome/blgnome4n1.htm")

Edit : did not see your last comment, Right click on your desktop & create a launcher for your terminal (above command) this may help you.

---

### Post by hiro nakamatty on 2008-06-14
i coded the gnome panel bit, it asked me to install it, so i did, and it seems to have done the trick
thanks all who helped me!

---

