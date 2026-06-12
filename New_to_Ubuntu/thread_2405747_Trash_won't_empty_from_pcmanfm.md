---
title: "Trash won't empty from pcmanfm"
date: 2018-11-10
forum: New to Ubuntu
---

### Post by cybervigilante on 2018-11-10
Lubuntu 18.10, LXQT - I have Trash on my quickaccess on pcman, but there is no right click to empty it and when I open it and try to delete it says Moving to Trash can, where it already is, then the delete fails. Is this a bug or is there a way to empty it (besides the terminal)?

 

 Also, how can I get something onto the launch bar on the bottom? I'd like to put leafpad there.

---

### Post by stephen-d-allen on 2018-11-10
What I'd do is install Bleachbit, run it as root and enable the 'delete trash' option and run it. Hopefully that does the trick. Good idea to run an app like Bleachbit regularly too, IMHO.

---

### Post by Dennis N on 2018-11-10
> is there a way to empty it (besides the terminal)?
See attached screenshot for how to empty trash. Secondary menu appears when you right-click on trash. (Sidebar must be set to show "Places", not "Directory Tree".)
> how can I get something onto the launch bar on the bottom?
I open the main menu, and left-click and hold to drag the menu entry for the application onto the quick launch bar.

---

### Post by MSGone on 2018-11-14
From the terminal:

rm -rf ~/.local/share/Trash/*

---

