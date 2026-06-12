---
title: "Ubuntu gone?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ajax010 on 2008-04-25
I'm an Ubuntu beginner.  My son set up a spare Dell desktop we had as an Open system in the summer, and I really like it - 7.1, Firefox and OpenOffice.

Today I booted the machine, logged onto Ubuntu, and nothing.... black screen, about 10 minutes of disk activity and now.... zilch.

Would it have tried to update to v8 automatically, and failed?

What do I do now?

---

### Post by acelin on 2008-04-25
Maybe your computer died. Try booting the live disk to see if it can even run that.

---

### Post by PmDematagoda on 2008-04-25
Did you try switching to a tty(Command Line Interface) by pressing Ctrl+Alt+F1? If it works, do:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
the command restores the X-Server settings to it's defaults. After that is done, do:-
```
sudo reboot
```
to reboot Ubuntu and see if the problem is now solved.

---

### Post by ajax010 on 2008-04-25
Doing it now, seems to be booting fine from the CD

---

### Post by ajax010 on 2008-04-25
It booted from the CD.  I removed the CD and rebooted from the HD - booted fine this time. ever had a problem (since Christmas).  Odd.

Thanks

---

### Post by Deathbeholdsyou on 2008-04-25
yeah that could be the problem
or make sure your CD\DVD Drives plugged completely in from inactivity, or make sure your hard drive is plugged in all the way. 
I made those mistakes |:
a couple of times

---

### Post by Deathbeholdsyou on 2008-04-25
nevermind
My helps not needed, I hate life. D:

---

