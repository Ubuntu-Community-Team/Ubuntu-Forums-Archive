---
title: "missing shut down option ?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by techno-mole on 2008-06-28
hello.

my system updated yesterday (nothing unusual) but last night when i went to shut down i noticed that the turn off button was missing from awn, ive got hibernate log out etc etc, but no option to turn off the system ?
 so i thought id see if it was a bug with awn and so i went to system -> quit, but sure enough it wasnt there either

i logged out to see if the option was at the log in window, and its missing from there as well, so basically if i want to shut down the system i have to press the power button, any ideas on how i can get it back ?

---

### Post by plucky on 2008-06-28
> any ideas on how i can get it back ?

Not sure how to fix your problem but instead of powering down from the button,open a terminal and ```
sudo shutdown -h now
``` should shut your system down.

Good Luck

---

### Post by tua03332 on 2008-07-05
I just had the same problem too, a possible fix is to go to system>admin>Login window  go to the local tab  about halfway down where it says Menu Bar, check the Show Actions Menu.  That should do it.

---

### Post by Troll_the_Great on 2008-07-05
I had the same problem and I solved it by reinstalling gdm.First open a terminal and type ```
gdm
``` and if it doesn't work try reinstalling it.
Cheers!

---

