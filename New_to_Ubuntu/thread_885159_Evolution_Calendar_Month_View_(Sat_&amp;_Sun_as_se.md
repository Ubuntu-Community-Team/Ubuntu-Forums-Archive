---
title: "Evolution Calendar Month View (Sat &amp; Sun as separate days)"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by raccoonone on 2008-08-09
Is there a way to change the Month View in Evolution so that it displays events for Sat & Sun as separate days, rather than grouping them into the same box?

---

### Post by anthropoidster on 2008-08-09
Yes - In Preferences - Calendar and Tasks, check all days under 'Work Days'.  That should do the trick (did for me).

---

### Post by raccoonone on 2008-08-09
For me that only included Sat & Sun in the Work Week view. They're still lumped together on the Month view

---

### Post by raccoonone on 2008-08-09
I figured out the answer to my problem. Open gconf-editor, then browse to apps > evolution > calendar > display, then uncheck compress_weekend

---

### Post by anthropoidster on 2008-08-09
Ok. How about Preferences - Calendar and Tasks - Display,  and uncheck 'Compress weekends in month view' - that's gotta be the one.

You beat me to it but I never tried it your way. Should mark this thread as solved.

---

### Post by celem on 2009-05-12
anthropoidster - thanks - that did it for me. It was driving me a bit nuts - I just couldn't "see" it. I have to print out the calendar for my computer averse wife and we have weekend appointments that need the full size boxes.
:)

---

