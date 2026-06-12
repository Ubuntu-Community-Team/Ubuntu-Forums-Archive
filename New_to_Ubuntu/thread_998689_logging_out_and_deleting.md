---
title: "logging out and deleting"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by gzav on 2008-12-01
Hey all,

i have the same problem as in this thread: [http://ubuntuforums.org/showthread.php?t=398781](http://ubuntuforums.org/showthread.php?t=398781) (xfce panel getting blocked on the left without being able to go back to default)

Apparently, the solution is to log out, delete the config directory and log back in. But, once i log out, i don't know how to delete that directory... and if i stay logged in, delete the directory and restart the computer, the directory is back and the problem too...

How should i delete a directory while being logged out?
(i'm using xubuntu on a usb key)

---

### Post by hellion0 on 2008-12-01
1. Log out.
2. At the login screen, press Control+Alt+F1. This should bring you to a screen with no graphics, just text on a black screen.
3. Log in if necessary with your username and password. Sometimes this step is not needed.
4. Issue the following command:
```
rm -r ~/.config
```
5. Press Control+Alt+F7. You should be back in a graphical environment, at the login screen. Use it to log in.
6. Your desktop should be back at the default.

---

### Post by gzav on 2008-12-01
It worked! Thanks a lot!

---

