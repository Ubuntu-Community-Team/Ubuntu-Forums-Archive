---
title: "login problem"
date: 2018-05-04
forum: New to Ubuntu
---

### Post by rburkartjo on 2018-05-04
when i was testing 18.04 ran into a bad update on one of the daily builds and lost the ability to log into a gnome session. can still log into xubuntu and lubuntu session. i have the final installed and still have the same problem. any ideas? also if i wait for 18.10 and upgrade would that fix the problem./tks

---

### Post by #&amp;thj^% on 2018-05-04
Have you tried installing or re-installing "ubuntu-session"
This package contains the required components for running a GNOME 3 session
with default Ubuntu configuration, based on the GNOME Shell. 
```
sudo apt install --reinstall  ubuntu-session
```
I myself have found installing more than 1 DE cause's some undesirable effects.
Best Of Luck.

---

### Post by rburkartjo on 2018-05-04
1fall yes and tried again but didnt fix problem.

---

### Post by #&amp;thj^% on 2018-05-04
I'm sorry to here that. :(
Sometimes when the login is broke for a session, I can from the "login window", instead of  entering my name and password>>I can just go to TTY session via: ctrl+alt+F2. (Note: (ctrl+alt+F1 dose not seem to work any longer))
And from there I then enter my user name and password and then enter** "startx" **this usually for me is enough to get to a Desktop session, If not the output in the terminal might shed some light on the problem.
**EDIT: I just was reminded that if using GDM instead of LightDM **I seen more login problems, so maybe that might help here. Or reconfigure lightdm again and try. (Shouldn't hurt anything as both XFCE and LXDE both use lightdm)

---

