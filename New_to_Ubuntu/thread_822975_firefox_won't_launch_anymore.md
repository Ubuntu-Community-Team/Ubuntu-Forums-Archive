---
title: "firefox won't launch anymore"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Matt26 on 2008-06-08
my computer froze up completely recently (no mouse movement, couldn't even use the Alt+Pr Scr.+REISUB method to reboot) so i had to use the reset button on the PC case... when i logged back into ubuntu (8.04) i noticed the icon for FF was replaced with a grey square on my taskbar (and no icon under Applications menu) so when i click on it the mouse pointer changes to the waiting icon for a few seconds and then nothing happens- if i try to open FF from the terminal window (just using the command 'firefox') same results.  can anyone tell me what to do to get FF working again?  thanks.

---

### Post by Joeb454 on 2008-06-08
Does the terminal provide any output when you try and start Firefox from there?

---

### Post by Matt26 on 2008-06-08
no, nothing comes up- just returns to the command prompt.

---

### Post by Matt26 on 2008-06-08
i just tried again from the terminal window and this time it took a few seconds before returning back to the comand prompt- still nothing happened, but i noticed the HDD LED on my PC case flicker a bit like it was trying to do something?

---

### Post by Bubba64 on 2008-06-08
You can do a few things have you tried the applications-internet-Firefox browser, have you tried another restart, have you looked in synaptic, have you hit reinstall in synaptic. If it shows the gray box in the panel it is probably gone although I don't know how or why. Have you looked in the home file-Mozilla to see if anything is there. Last you also have alt f2 and click on FF browser then run

---

### Post by Matt26 on 2008-06-09
i have tried using the launcher under the Applications menu and it does the same thing (no response) and i have restarted a few times now and no changes yet... i have considered going into add/remove programs (as opposed to synaptic- is there a difference?) and removing it from there and then reinstalling it but i wasn't sure if this would remove my settings that i have setup for FF including my Bookmarks, page history etc.  can anyone confirm this?  what is the home file- Mozilla that you are referring to?  i'm not familiar with it.  thanks.

---

### Post by miss.magenta on 2008-06-09
it would be in /home/username/.mozilla/firefox/somefunkynumber.default

at the very least, copy the bookmarkbackups directory to preserve your bookmarks if you reinstall

---

