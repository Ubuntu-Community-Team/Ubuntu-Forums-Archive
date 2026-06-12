---
title: "trouble while getting the xserver"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by shashank.ks on 2008-06-22
I install the ubuntu few days back. I was able to start and do every thing with it. But now suddenly now i am getting blank screen when i start the my computer with my wall paper. key board is not working mouse is not working.
i get this problem with only the xterminal. I can login and use all the other commands in other terminals. In the xterminal i get only blank screen with my wall paper. I am not getting any error message also.

---

### Post by pytheas22 on 2008-06-22
Can you log in to a failsafe session?  In the bottom-left corner of the screen there's a menu that you can click to select a failsafe session.  Please let us know whether that works.

---

### Post by shashank.ks on 2008-06-22
i tried that too. but it has the same problem as the earlier one. but i can log in to the terminal mode present there. it gives an xterm to use. form there i can launch the fire fox and all the other application. But these applications wont have any borders and i can launch one application at a time and i have to close the old one to launch new one.

---

### Post by pytheas22 on 2008-06-22
Alright, then please try this to refresh your gnome configuration:
```

mv ~/.gnome ~/.gnome-OLD
mv ~/.gnome2 ~/.gnome2-OLD
```

and see if this helps.

> i have to close the old one to launch new one.

Just on a side note, if you put a & at the end of the command (i.e., type "firefox &" and press enter), you should be able to launch more than program.  This is just a good thing to know about Linux.

---

### Post by shashank.ks on 2008-06-24
It worked.:) Thnaks for the help.

---

