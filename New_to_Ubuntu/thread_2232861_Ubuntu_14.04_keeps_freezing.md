---
title: "Ubuntu 14.04 keeps freezing"
date: 2014-07-04
forum: New to Ubuntu
---

### Post by jordan23 on 2014-07-04
I am not really sure on what is happening but my laptop keeps freezing  on me. This has been happening for a few days now, and I notice that it  happens when I am loading a Youtube video or downloading something.  Usually I would hit Ctrl + alt + t to get out of a frozen screen and it  helped but now I am finding it doesn't help anymore. What usually does  help is when I go into TTY1. It's manageable but annoying that my laptop  keeps freezing up like that. My laptop is an ASUS ultrabook S56C. Do  you have any suggestions on what might be causing my laptop to freeze? I was told it might be a graphics card problem. 

[ATTACH=CONFIG]254467[/ATTACH][ATTACH=CONFIG]254468[/ATTACH]

---

### Post by Vladlenin5000 on 2014-07-05
Have you tried 331-updates already?

---

### Post by jordan23 on 2014-07-05
yup, it still freezes.

---

### Post by waterlubber on 2014-07-06
I had a similar issue. Apparently, adobe flash can run into a bug where it pretty much sets your CPU on fire...:P When watching videos, don't scroll around. Apparently that causes the bug for me.

---

### Post by Ashwij on 2014-07-07
I would suggest the best way to fix this is to enable pre release updates in Software and Updates and then run sudo apt-get update && sudo apt-get upgrade.

Then check if any proprietary drivers present for the video card and the wireless(I am assuming its on wifi).

Should surely fix the problem.

Also if it is Firefox / Chrome u are using, do a ctrl+shift+delete before closing the window or simply use bleachbit.

---

