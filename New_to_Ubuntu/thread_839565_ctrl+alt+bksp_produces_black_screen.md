---
title: "ctrl+alt+bksp produces black screen"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-06-24
Hey everyone,

Whenever I hit ctrl+alt+bksp my screen goes black.. and that's the end of it. Then I have reboot my computer.

Any ideas what could be wrong?

---

### Post by avtolle on 2008-06-24
That command shuts down the X server. This is how the system is set up. To get back, do CTRL+ALT+F7.

---

### Post by markjensen on 2008-06-24
Not sure.  It should kill X, then your gdm should kick in and show you the login screen again.

Did the login screen work when you first boot and login?

Alternatively to CTRL+ALT+BS, and you open a terminal and do a **sudo init 3** which will kick to to text mode.  You should have a bash prompt there.  To fire back up your gui, a **sudo init 5** should do the trick.

Let's see if those work at all.

---

### Post by avtolle on 2008-06-24
> **markjensen said:**
> Not sure.  It should kill X, then your gdm should kick in and show you the login screen again.

Did the login screen work when you first boot and login?

Alternatively to CTRL+ALT+BS, and you open a terminal and do a **sudo init 3** which will kick to to text mode.  You should have a bash prompt there.  To fire back up your gui, a **sudo init 5** should do the trick.

Let's see if those work at all.
You're correct, that is what should happen.

---

### Post by mishathegoat on 2008-06-24
EDIT: Thanks guys I'll give it a shot

Also note that it's just a plain black screen, no command line, no nothing

---

### Post by mishathegoat on 2008-06-24
> **markjensen said:**
> Not sure.  It should kill X, then your gdm should kick in and show you the login screen again.

Did the login screen work when you first boot and login?

Alternatively to CTRL+ALT+BS, and you open a terminal and do a **sudo init 3** which will kick to to text mode.  You should have a bash prompt there.  To fire back up your gui, a **sudo init 5** should do the trick.

Let's see if those work at all.

Yep the login screen works each time I boot up

---

### Post by markjensen on 2008-06-24
No.  It is not normal, silly.  :P

That is why we are asking for a few things to check.  It may be that the video card (for whatever reason) is outside the range of displayable modes for your monitor.

Using CTRL+ALT+F2-F7 may help in-so-far as you should get text logins all the up to CTRL+ALT+F7, as posted before by avtolle.   If you try some of the steps and the screen goes "blank", try switching to the other TTYs and see if you get text logins and your GUI back in their proper locations.

---

