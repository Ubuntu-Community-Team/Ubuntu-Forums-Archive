---
title: "Python timer?"
date: 2006-04-15
forum: Programming Talk
---

### Post by idn on 2006-04-15
Hi 

I am creating a mail notification applet, and I have done pretty well so far, i have made the app get new mesages and display a notification but have to way to set this to a timer, so it polls the mail server x numner of seconds

Does anyone have any suggestions on how to do this?

Thanks!

---

### Post by doclivingston on 2006-04-15
Assuming you're using PyGTK:

```
import gobject

gobject.timeout_add (60 * 1000, function, ...)

def function (...):
    #do stuff here
    return False
```

That will cause function() to get run in (about) a minutes time, being 60000 miliseconds. Returning False make it not run again, and the function will get run in another minute if you return True.

See [http://www.pygtk.org/pygtk2reference/gobject-functions.html#function-gobject--timeout-add](http://www.pygtk.org/pygtk2reference/gobject-functions.html#function-gobject--timeout-add) for more info.

---

### Post by fng on 2006-04-15
Pygame also has a time class: [http://www.pygame.org/docs/ref/time.html](http://www.pygame.org/docs/ref/time.html)

---

