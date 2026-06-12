---
title: "Ubuntu freezing on login"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Hobo Joe on 2008-07-02
So, the other day while I was going to be away from the computer, I started a rather large render in Blender. I walked away from the computer and came back hours later and the screen was black and I could get nothing from the computer. I tried restarting X and falling back to the command line, but nothing worked. So, I had to force reboot it. 

It loaded up fine, and I got the login screen, and logged in. Then I got the normal brown screen that you get after logging in, but it didn't go away. After about 20 seconds, a small grey box appeared in the top left corner of the screen. Then it just froze. I can restart X and do it again, with the same result. 

I've tried starting different sessions, even failsafe GNOME doesn't work properly. In fact, the only one that DOES work is failsafe Terminal. I've tried everything I can think of, including re-installing the video drivers, but nothing has worked. 

Any ideas?

---

### Post by Darkade on 2008-07-05
what happens if you login in a failsafe terminal and type
```
sudo gdm
```
or ```
nautilus
```
?

---

