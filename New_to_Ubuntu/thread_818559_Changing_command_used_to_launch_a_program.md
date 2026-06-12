---
title: "Changing command used to launch a program"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-06-04
This refers specifically to Wicd, I'd like to be able to start it in the command line by typing something like 'wicd' rather than '/opt/wicd/gui.py'.  I don't know if I'd need a bash script to reroute a 'wicd' command to run that other command, or if there's a simple command to do that.  Or if I need to make a copy of the program somewhere else under a different name.  Any help would be greatly appreciated.

Thank you.

---

### Post by wpshooter on 2008-06-04
Is this what you are looking for ?

[http://www.mediacollege.com/linux/command/alias.html](http://www.mediacollege.com/linux/command/alias.html)

---

### Post by Steveway on 2008-06-04
Just make a symlink called wicd that points to it and place it into /usr/bin. (You'll need superuser-access to do that.)

---

### Post by ConMan318 on 2008-06-04
The alias command worked.  I hadn't heared of a symlink before, I've just been looking them up, and maybe I'll (try to) make one later.  Thanks to you both.

---

