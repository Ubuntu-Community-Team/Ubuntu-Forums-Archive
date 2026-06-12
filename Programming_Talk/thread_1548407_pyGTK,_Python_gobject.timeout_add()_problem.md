---
title: "pyGTK, Python gobject.timeout_add() problem"
date: 2010-08-08
forum: Programming Talk
---

### Post by Jefferythewind on 2010-08-08
Hi everyone,
  I am making a little application that reads serial data and then draws on a gtk.DrawingArea.  I get the out put from an accelerometer.  Anyways, I want to make this application refresh automatically, so it will be like a small animation.  I searched around the web and found:

gobject.timeout_add(ms, fn)

and I have seen some examples, but when i run my code I get this error:

```
self.timer = gobject.timeout_add(10, draw_vector())
NameError: global name 'gobject' is not defined
```

I have tried using:
```

window.timeout_add(10, draw_vector())

```

but it doesn't work either

I have attached my python script and the line in question is 108.

thanks for any help.

---

### Post by StephenF on 2010-08-08
import gobject

---

### Post by Jefferythewind on 2010-08-08
omg, thank you.

---

### Post by Jefferythewind on 2010-08-08
OK, well I got rid of that problem, and I am not getting any errors, I set up the timer at the end of the main loop, but my function is not being called by the timer.  Does anyone have any ideas?

I attached the code again.

---

### Post by StephenF on 2010-08-08
From
```

gobject.timeout_add(10, draw_vector(drawing_area))

```
To
```

gobject.timeout_add(10, draw_vector, drawing_area)

```
What your code currently does is call draw_vector once and then passes the returned object to timeout_add. In this case, None. Also your callback needs to return True if you want it to be repeatedly called.

One other minor change is that the real home of timeout_add appears to be the glib module. Expect access of timeout_add via the gobject module to disappear at some point in the future. Import glib instead.

---

### Post by Jefferythewind on 2010-08-08
Thanks a lot for the help.  I see what you are saying.  I haven't had a chance to test it out yet, but I'll post the results when I do.

---

