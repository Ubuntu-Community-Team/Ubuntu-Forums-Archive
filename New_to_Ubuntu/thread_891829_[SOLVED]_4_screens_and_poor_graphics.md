---
title: "[SOLVED] 4 screens and poor graphics?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by lyleandrose on 2008-08-16
I am an absolute beginner.   

I started Gutsy (7.10) today.   After the Unbuntu load bar  I get
4  identical small Unbuntu front page screens and cursers in the upper 3/4 of the screen and some colored bars at the bottom.  The start page screens are so faint and hard to read that I can't go to the submenus to change anything. What's up?   Can I change the graphics back by going to the console?

Thanks,
Lyle

---

### Post by Sam Lars on 2008-08-16
You could try Ctrl+Alt+Backspace to restart the graphical interface.  Ctrl+Alt+F1 will get you to a terminal that you can log into.

---

### Post by jualin on 2008-08-16
And then you can also try reconfiguring xorg when you are on the console (CTRL-ALT-F1). Log in (using the terminal) and type > sudo dpkg-reconfigure xserver-xorg and follow the instructions. Then go back to the Log in window with CTRL-ALT-F7. Hope this helps!

---

### Post by lyleandrose on 2008-08-16
The control alternate backspace gives me a blank black page and nothing else.

From the console I typed sudo dpkg-reconfigure xserver-xorg and got to a new page.
On page one the progam idetified my intel board 
On page two it identified my chipset graphics device
On page three ( configuring xserver-xorg it freezes and won't let me move on even though the "ok" appears at the bottom.   To restart the computer I must push the reset button. 

Um! Any other ideas?

---

