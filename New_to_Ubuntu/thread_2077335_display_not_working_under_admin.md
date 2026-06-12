---
title: "display not working under admin"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by saaju on 2012-10-28
Hey there, i'm new with Ubuntu and apparently I clicked something I shouldn't.
I'm using my TV as a monitor because the screen in my laptop its broken, I clicked a button in the display settings and now I can't see anything, TV screen went black
it only works when i'm logged in as invited and not admin. Is there any way this can be fix without beign admin or can I fix it using terminal as a non admin user?
Can somebody please help me?

---

### Post by coffeecat on 2012-10-28
Not a testimonial.

*Thread moved to **Absolute Beginners Section***

---

### Post by saaju on 2012-10-28
Hey guys, just in case somebody has the same problem, I fixed mine.
I restored the default settings on terminal and happily nothing was erased just the desktop background and some icons there.

This is the command I used in Terminal:

rm -r ~/.config/ ~/.cache/


note: Do not log-in as invite, run terminal from the log-in area by clicking ctlr+alt+f2. When you're done you can get out of terminal by clicking cltr+alt+del

---

