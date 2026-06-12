---
title: "Failed Log-in"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by prifer on 2008-08-19
Hi again!

this morning as usual come to my office and start open my laptop, I was trying to log in, type my username and password but the screen went blank (green) and looks like stop working, i shut it down and repeat again but still that green blank screen appears, so now i am back again using Windows

please your advice. thanks

---

### Post by Separ on 2008-08-19
Have you tried giving it the old ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` in recovery mode? :)

---

### Post by prifer on 2008-08-19
it still doesnt work:(

---

### Post by alienexplorers on 2008-08-19
At the green screen try this:
> Press Ctrl+Alt+F1

You will be dropped to a screen where you can log in as root.

Once logged in, then do

passwd <username>

This will allow you to set a new password for the <username>

Once done, you can press Ctrl+Alt+F9 to return to your X session.

Hope this helps.

---

