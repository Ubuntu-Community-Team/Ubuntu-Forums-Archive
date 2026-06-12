---
title: "Possible to launch a terminal that starts a program from a launcher?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by FreewareFan on 2008-06-21
Would it be possible for me to create a desktop launcher that starts gnome-terminal and has that terminal run the htop application from just one icon?  I tried using "gnome-terminal htop" in the launcher's properties, but that did not work.

Thanks for any suggestions!

---

### Post by sdennie on 2008-06-21
Try:

```

gnome-terminal -e htop

```

Or, there is an option in the launcher configuration (at the top) that allows you to specify that it's a terminal application and will do this for you (you won't need gnome-terminal just "htop").

---

### Post by forestpixie on 2008-06-21
When you make the launcher - there is a drop down menu which allows you to run an app in terminal

command for app needs to be htop

Edit - snap :)

---

### Post by FreewareFan on 2008-06-21
Worked beautifully!  Many thanks to you both.

---

