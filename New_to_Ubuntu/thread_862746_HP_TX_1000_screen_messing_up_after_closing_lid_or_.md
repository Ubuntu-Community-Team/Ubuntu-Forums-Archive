---
title: "HP TX 1000 screen messing up after closing lid or leaving it alone for too long"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by SlingerXL on 2008-07-17
Every time I leave my HP tx 1000 alone for around 10 minutes, when I open it up again the screen gets dozens of faint vertical bars, the resolution messes up either becoming too short or too long so it's of the display, it slows down a lot, the mouse becomes choppy, and I can't read text on it because all the text is messed up. It's like certain parts of characters are too thick and others are too thin making it unreadable.

Any idea what's causing this?

---

### Post by seagullplayer77 on 2008-07-17
I've found that sometimes going into a vertical terminal (Ctrl+Alt+F1) and then going back to your desktop (Ctrl+Alt+F7) sometimes helps with display problems. If that doesn't work, the only other thing I can think of is restarting X, aka logging out and logging back in. As to what's causing your problems, I really haven't the foggiest idea. Sorry I couldn't be more helpful...

---

### Post by TSS on 2008-07-17
> **SlingerXL said:**
> Every time I leave my HP tx 1000 alone for around 10 minutes, when I open it up again the screen gets dozens of faint vertical bars, the resolution messes up either becoming too short or too long so it's of the display, it slows down a lot, the mouse becomes choppy, and I can't read text on it because all the text is messed up. It's like certain parts of characters are too thick and others are too thin making it unreadable.

Any idea what's causing this?

I have this problem on my tx1220 and I believe it's the nVidia driver.  It happens when your display gets put to sleep, correct? Typing CTRL+ALT+Backspace to restart X fixes the problem.  I also think upgrading to the newest version of the driver through Envy does the job as well, although I haven't tried it.

---

